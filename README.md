# configure_webservers_with_jinja_template
🌐 Deploy webpage to two different webservers and display the OS name and Kernel version in the webpage 🌐

Introduction:

To fulfill the task, it is required to configure the web package and then deploy the webpage

Requirements:

- Two virtual machines created in Oracle Virtual box or two managed nodes created in AWS
- Controller node with ansible installed and configured

Tasks:

- Add the IP address or alias of the managed nodes which will be used as webserver and test the connection
- In the controller node, start developing the playbook.
- Write the 1st task to install the "httpd" package
- Write the 2nd task to create a directory. That need to be used document root which is different from /var/www/html location
- Create an webpage with following content and write the task with "template" module to place it to new defined document root.

This is the new webpage!!!!

The OS is: {{ ansible_facts.distribution }}
The kernal version is: {{ ansible_facts.kernel }}

Here, ansible_facts is a default variable in ansible which contains the information of software and hardware of the machine. ansible_distribution is sub-parameter which is used to display the OS name installed in the machine and ansible_kernel is the another sub-parameter to display the kernel version. The jinja template has been used here to declare the variables.

#Note: Template module will consider the jinja template and it will replace the content within {{ }} with its actual value which is not the case for copy module. It used to consider the entire content as collection of string and transfer it to the target location as it is.

- As per the requirement, a new configuration file need to be prepared to have the document root as /var/www/newweb and port as 81 which need to be placed in /etc/httpd/conf.d location. Write the task in the same way
- Write the task, to start the webservice with service module. The service need to be started at the end of all configuration.
- At the end, a handler has been written which is mentioned to be called if there is any change in webpage or configuration file. 
