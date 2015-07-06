# juju-charms
Juju Charms for Mobicents Components

# Deploying the charms 


    #boostrap Juju environment
    juju bootstrap
    #get logs
    juju debug-log
    # deploy juju gui
    juju deploy juju-gui
    #expose juju-gui for public access
    juju expose juju-gui

#Deploying RestComm Local Charm

    #deploy backend DB
    juju deploy mysql
    #deploy Mobicents RestComm Unit
    juju deploy -u --repository=../../ local:trusty/mobicents-restcomm
    #connect RestComm to the backend DB
    juju add-relation mobicents-restcomm mysql
    juju expose mobicents-restcomm

#Test RestComm Charm

Go to http://<public_ip>:8080/restcomm-management or http://<public_ip>:8080/restcomm-management (username: administrator@company.com, password: RestComm) for Admininstration

Go to http://<public_ip>:8080/olympus for WebRTC P2P Live Video chat
