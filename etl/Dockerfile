FROM python:3.12

# Add PostgreSQL APT repository for version 16
RUN apt-get update && apt-get install -y wget gnupg && \
    wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add - && \
    echo "deb http://apt.postgresql.org/pub/repos/apt bookworm-pgdg main" > /etc/apt/sources.list.d/pgdg.list && \
    apt-get update && apt-get install -y postgresql-client-16 && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Copy the ELT script
COPY etl_script.py .

# Set the default command to run the ELT script
CMD ["python", "etl_script.py"]
