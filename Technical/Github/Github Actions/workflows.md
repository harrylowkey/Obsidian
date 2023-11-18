#technical  #github

Sample:
```python
name: ci

on:
  push:
    branches:
      - "develop"
jobs: 
  test:
    runs-on: ubuntu-latest
    timeout-minutes: 10
    services:
      postgres:
        image: postgis/postgis:11-3.3
        env:
          POSTGRES_DB: renyoo_unit_test
          POSTGRES_USER: test
          POSTGRES_PASSWORD: test
          POSTGRES_HOST_AUTH_METHOD: trust
        ports:
          - 5432:5432
        options: >-
          --health-cmd pg_isready
          --health-interval 10s
          --health-timeout 5s
          --health-retries 5
      redis:
        image: redis
        options: >-
          --health-cmd "redis-cli ping"
          --health-interval 10s
          --health-timeout 5s
          --health-retries 5
        ports:
          - 6379:6379
      maildev:
        image: maildev/maildev
        ports:
          - 1025:1025
    steps:
      - name: Check out repository code
        uses: actions/checkout@v2

      - name: Setup Python
        uses: actions/setup-python@v2
        with:
          python-version: "3.10"

      - name: Install Package
        run: |
          python -m pip install --no-cache-dir --upgrade -r requirements.txt -no-dependencies

      - name: Check format
        run: |
          flake8 src

      - name: Run e2e test
        env:
          AWS_SECRET_KEY: ${{ secrets.AWS_SECRET_KEY }}
          KEYCLOAK_CONFIDENTIAL_CLIENT_SECRET: ${{secrets.KEYCLOAK_CONFIDENTIAL_CLIENT_SECRET }}
          TWILIO_AUTH_TOKEN: ${{ secrets.TWILIO_AUTH_TOKEN }}
        run: |
	        cp .env.unit-test .env
	        alembic upgrade head
	        pytest
  build:
    runs-on: ubuntu-latest
    steps:
      -
        name: Checkout
        uses: actions/checkout@v3
      -
        name: Login to Docker Hub
        uses: docker/login-action@v2
        with:
          username: ${{ secrets.DOCKERHUB_USERNAME }}
          password: ${{ secrets.DOCKERHUB_TOKEN }}
      -
        name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v2
      -
        name: Build and push
        uses: docker/build-push-action@v4
        with:
          context: .
          file: ./Dockerfile
          push: true
          tags: ${{ secrets.DOCKERHUB_USERNAME }}/clockbox:latest
```