set +o history


3. Install Google App Engine and Create a Hello World App (Python/Java):

To set up Google App Engine (GAE) on your machine:

    Install Google Cloud SDK:
        Follow the instructions to install the Google Cloud SDK.
        After installation, initialize the SDK:

    gcloud init

Create a Python App:

app.yaml:

runtime: python310
entrypoint: gunicorn -b :$PORT main:app

main.py (Simple Python Web App):

from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello():
    return 'Hello, World!'

if __name__ == '__main__':
    app.run(debug=True)

Install Flask:

pip install Flask

Deploy the App to Google App Engine:

    Deploy using:

        gcloud app deploy

    You can now access your "Hello, World!" app on the URL provided by Google Cloud.

4. Use the GAE Launcher to Launch Web Applications:

Google App Engine Launcher (for Python apps):

    If you're on Windows or macOS, you can use the GAE launcher to test your apps locally before deploying them.
    To launch the app locally:

    dev_appserver.py app.yaml

    Open the local URL (typically http://localhost:8080/), and you should see the "Hello, World!" message.

5. Simulate a Cloud Scenario Using CloudSim and Run a Scheduling Algorithm:

CloudSim is a framework for simulating cloud computing environments. You can add your own scheduling algorithms.

Steps to Run CloudSim:

    Download and set up CloudSim: CloudSim GitHub
    Implement a custom scheduling algorithm:
        Extend the CloudletScheduler class.
        Override the scheduling method to implement your custom scheduling logic.

Example Java Code for a Simple Custom Scheduler:

import org.cloudbus.cloudsim.*;
import org.cloudbus.cloudsim.core.*;
import org.cloudbus.cloudsim.schedulers.*;

public class CustomScheduler extends CloudletScheduler {
    @Override
    public void cloudletSubmit(Cloudlet cloudlet) {
        // Custom scheduling logic here
        // For example, FIFO scheduling or Round-Robin
        super.cloudletSubmit(cloudlet);
    }
}

6. Transfer Files from One Virtual Machine to Another:

Option 1: Using SCP (Secure Copy Protocol):

    Enable SSH on both VMs.
    Use scp to copy files between them:

scp /path/to/local/file user@remote:/path/to/destination

Option 2: Shared Folders in VirtualBox:

    Set up shared folders in VirtualBox for direct file access between VMs.
        Go to VM settings → Shared Folders → Add a new shared folder.

7. Install Hadoop Single Node Cluster and Run Word Count Example:

Steps to Install Hadoop on Ubuntu:

    Install Java and Hadoop Dependencies:

sudo apt update
sudo apt install openjdk-8-jdk
sudo apt install ssh
sudo apt install hadoop

    Configure Hadoop:
        Modify the Hadoop configuration files (core-site.xml, hdfs-site.xml, mapred-site.xml) as needed for a single-node setup.

    Start Hadoop and Run WordCount Example:
        Format the Hadoop filesystem:

hdfs namenode -format

    Start HDFS and YARN:

start-dfs.sh
start-yarn.sh

    Upload input file:

hdfs dfs -put inputfile /input

    Run WordCount:

    hadoop jar /usr/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar wordcount /input /output

    View Results:

hdfs dfs -cat /output/part-r-00000

8. Creating and Executing Your First Container Using Docker:

Steps to Create and Run a Docker Container:

    Install Docker:
        Follow the Docker installation guide for your system: Docker Install.

    Create a Dockerfile:

    Dockerfile Example (Python):

    FROM python:3.10-slim

    WORKDIR /app

    COPY . .

    RUN pip install -r requirements.txt

    CMD ["python", "app.py"]

    Build the Docker Image:

docker build -t my-python-app .

    Run the Container:

docker run -d -p 5000:5000 my-python-app

9. Run a Container from Docker Hub:

Steps to Pull and Run a Pre-built Container:

    Search for a Docker image on Docker Hub:

docker search <image-name>

    Pull an image (e.g., nginx):

docker pull nginx

    Run the Container:

docker run -d -p 8080:80 nginx

Your Nginx web server will be available at http://localhost:8080.
