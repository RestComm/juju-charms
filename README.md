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
If you have juju-quickstart https://launchpad.net/juju-quickstart to deploy and connect to juju GUI use this one command for current bootstrapped envrioment. See also: https://github.com/juju/cheatsheet

    juju-quickstart     


#Deploying RestComm
There is now 2 options for deploying RestComm :

##0. Download this project
As a temporary solution till this bundle and charms will be in charm store: jujucharms.com we are using local deployment

    git clone https://github.com/Mobicents/juju-charms.git



##1. Manual way - Deploying MySQL and RestComm Charms

    #deploy backend DB
    juju deploy mysql
    #if you use juju local (ie lxc - https://jujucharms.com/docs/stable/config-local) as environment mysql needs this below
    #juju set mysql dataset-size='512M'
    #juju resolved -r mysql/#
    #deploy Mobicents RestComm Unit (the same folder where you issued git clone command)
    juju deploy -u --repository=juju-charms/mobicents-restcomm-charm/ local:trusty/mobicents-restcomm 
    #connect RestComm to the backend DB
    juju add-relation mobicents-restcomm mysql
    juju expose mobicents-restcomm

##1. Automated way (to be verified) - All Integrated Bundle
Import https://raw.githubusercontent.com/Mobicents/juju-charms/master/mobicents-restcomm-mysql.yaml through the Juju GUI that you just deployed previously

#Test RestComm Charm

Go to http://<public_ip>:8080  (username: administrator@company.com, password: RestComm) for Admininstration

## WebRTC call

Go to http://<public_ip>:8080/olympus for WebRTC P2P Live Video chat

Please refer to this link: http://caniuse.com/#search=webrtc  for the most up-to-date information about browser WebRTC support.

## Clean enviroment  
When you done, you can clean ennviroment and destroy all services (do not terminate machines). 

    juju-deployer -D 
