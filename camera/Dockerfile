# Stage 1: Base
FROM python:3.9-slim as base
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .

# Stage 2: Test
FROM base as test
RUN pip install --no-cache-dir pytest
CMD ["python", "-m", "pytest", "--maxfail=1", "--disable-warnings", "-q"]

# Stage 3: Runtime
FROM base as runtime
CMD ["python", "app.py"]
