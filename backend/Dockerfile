#dockerfile for groser store managemnent system 
#python app dockerfile
#FROM python:3.10.5

#WORKDIR /gsms

#COPY requirements.txt requirements.txt
#RUN pip3 install -r requirements.txt

#COPY . .
#EXPOSE 5000

#CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0"]


FROM python:3.10.5-slim

WORKDIR /gsms

# Install required packages
RUN apt-get update && apt-get install -y \
    build-essential \
    default-libmysqlclient-dev \
    && rm -rf /var/lib/apt/lists/*

# Copy the requirements file and install the Python dependencies
COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

# Copy the application code
COPY . .

# Set the environment variables for MySQL connection
ENV MYSQL_DATABASE=grocery_store
ENV MYSQL_USER=root
ENV MYSQL_PASSWORD=thangamey143
ENV MYSQL_HOST=localhost
ENV MYSQL_PORT=3306

# Expose the port on which the Flask app is running
EXPOSE 5000

# Start the application
CMD ["python", "app.py"]
