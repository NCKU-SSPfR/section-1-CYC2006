# Specify Base Image
FROM python:3.11

# Create a new User, create his home directory
RUN useradd -m appuser

# Set Work Directory
WORKDIR /app

# Copy requirements.txt from the host to the current directory inside the container (/app)
COPY requirements.txt .

# Use pip to install all Python dependencies in requirements.txt
# --no-cache-dir prevent pip from saving temporary files while installing, reduce file volume
RUN pip install --no-cache-dir -r requirements.txt

# copy machines src/ to /app/src
COPY src/ /app/src

# change all contents' user to appuser
RUN chown -R appuser:appuser /app

# User: root -> appuser
USER appuser

# Docker Container's application will run on port 8000
EXPOSE 8000

# Set the command to be excuted when the container starts
CMD ["uvicorn", "src.main:app", "--host", "0.0.0.0", "--port", "8000",  "--reload"]