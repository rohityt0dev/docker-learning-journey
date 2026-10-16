# FROM
FROM ubuntu:24.04

# ENV: Environment variables
ENV APP_ENV=production

# WORKDIR: Set working directory
WORKDIR /app

# RUN: Execute commands during image build
RUN apt-get update && apt-get install -y python3 curl

# COPY: Copy application files
COPY index.html /app/index.html

# EXPOSE: Document the application port
EXPOSE 8080


# HEALTHCHECK: Check application health
HEALTHCHECK --interval=30s --timeout=5s \
    CMD curl -f http://localhost:8080/ || exit 1

# ENTRYPOINT: Main executable
ENTRYPOINT ["python3", "-m", "http.server"]

# CMD: Default arguments for ENTRYPOINT
CMD ["8080", "--bind", "0.0.0.0"]
~
~
