Juju Charms for Mobicents Components

# Deploying/Starting Juju


    #boostrap Juju environment
    juju bootstrap
    #get logs
    juju debug-log
    # deploy juju gui
    juju deploy juju-gui
    #expose juju-gui for public access
    juju expose juju-gui
    
### juju-quickstart option
If you have juju-quickstart to deploy and connect to juju GUI use this one comment for current bootstrapped envrioment

    juju-quickstart     


#Deploying RestComm
There is now 2 options for deploying RestComm :

##1. Automated way - All Integrated Bundle
Import https://raw.githubusercontent.com/Mobicents/juju-charms/master/mobicents-restcomm-mysql.yaml through the Juju GUI that you just deployed previously

##2. Manual way - Deploying MySQL and RestComm Charms

    #deploy backend DB
    juju deploy mysql
    #if you use juju local (ie lxc - https://jujucharms.com/docs/stable/config-local) as environment mysql needs this below
    #juju set mysql dataset-size='512M'
    #juju resolved -r mysql/#
    #deploy Mobicents RestComm Unit
    juju deploy -u --repository=../../ local:trusty/mobicents-restcomm
    #connect RestComm to the backend DB
    juju add-relation mobicents-restcomm mysql
    juju expose mobicents-restcomm

#Test RestComm Charm

Go to http://<public_ip>:8080/restcomm-management or http://<public_ip>:8080/restcomm-management (username: administrator@company.com, password: RestComm) for Admininstration

Go to http://<public_ip>:8080/olympus for WebRTC P2P Live Video chat

## Clean enviroment  
When you done, you can clean ennviroment and destroy all services (do not terminate machines). 

    juju-deployer -D 
