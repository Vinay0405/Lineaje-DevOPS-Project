For the Project i have created the docker file separately 

The demo docker file that has taken as dummy 

# Use the official Python image as the base image
FROM python:3.9
# Set the working directory in the container
WORKDIR /app
# Copy the Python dependencies file to the container
COPY requirements.txt .
# Install the Python dependencies
RUN pip install --no-cache-dir -r requirements.txt
# Copy the Flask application code to the container
COPY app.py .
# Expose the port the Flask application will run on
EXPOSE 3000
# Command to run the Flask application when the container starts
CMD ["python", "app.py"]

After having the docker file following commands are used:

-----------------------------------------------------------------------------------------------------------------------------------------
aws ecr get-login-password --region eu-west-1 | docker login --username AWS --password-stdin 028857548531.dkr.ecr.eu-west-1.amazonaws.com
-------------------------------------------------------------------------------------------------------------------------------------------

---------------------------
docker build -t vinay-test .
---------------------------

After the build completes, tag your image so you can push the image to this repository:

------------------------------------------------------------------------------------------
docker tag vinay-test:latest 028857548531.dkr.ecr.eu-west-1.amazonaws.com/vinay-test:latest
-------------------------------------------------------------------------------------------

Run the following command to push this image to your newly created AWS repository:

-----------------------------------------------------------------------------
docker push 028857548531.dkr.ecr.eu-west-1.amazonaws.com/vinay-test:latest
----------------------------------------------------------------------------
