# NSO_a2
#NETWORK AUTOMATION

deployed a simple python flask app on 3 webservers and HAproxy server as a Loadbalancer. But instead of direct deployment , automated the whole the process using ansible.


Note:

-playbook script mentions webservers service deployment using both traditional flask deployment and also using a (production-ready)gunicorn deployement (one of them is commented out) . But for ideal production servers , it is better to use an external service instead of traditional flask deployment, because external services like gunicorn, uWSGI are designed to handle multiple http requests and also they can handle higher traffic load whereas the traditional flask deployement is a single threaded applications and is usually used for testing a single-webserving applications but cannot be used as production servers.

#REQUIREMENTS:
(tested in ) Ubuntu 22.04.2 LTS // ansible-base==2.10.8 //  pip 22.0.2 (python 3.10) //


****** NEW UPDATE - FLASK-GUNICORN IS INITIATED AS A SERVICE IN ANSIBLE SCRIPT *******

In previous version of this project, in ansible script (site.yaml) the flask-gunicorn service is initiated as a systemd service instead of running through the shell.
In a production environment, runnning through systemd is always preferred rather than shell due to multiple reasons. Here are the few reasons:
- If the if any service was initiated with systemd that service would automatically restarting when the server restarts or if the service crashes due to some other reasons, where as in shell we have to manually restart the service through shell again.
- To run a service through systemd we need a unit file (i.e., a .service file here) to start the service, so only the administrator could access the file. So, starting a service through systemd is more secure than starting through a shell
- And services deployed through systemd are always logged ( we can check through command - journalctl -u <unit-file>) , so that it is easier to monitor and trouble shoot the deployment of the service.

**************************************************************************************


 
