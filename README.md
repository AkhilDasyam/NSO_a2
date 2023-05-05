# NSO_a2
#NETWORK AUTOMATION

deployed a simple python flask app on 3 webservers and HAproxy server as a Loadbalancer. But instead of direct deployment , automated the whole the process using ansible.


Note:

-playbook script mentions webservers service deployment using both traditional flask deployment and also using a (production-ready)gunicorn deployement (one of them is commented out) . But for ideal production servers , it is better to use an external service instead of traditional flask deployment, because external services like gunicorn, uWSGI are designed to handle multiple http requests and also they can handle higher traffic load whereas the traditional flask deployement is a single threaded applications and is usually used for testing a single-webserving applications but cannot be used as production servers.
