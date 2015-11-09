# juju-charms
Juju Charms for Mobicents Components

##2. Automated way - Juju Charm Store
Import https://jujucharms.com/u/jean-deruelle/mobicents-restcomm-charm/ and https://jujucharms.com/mysql/ through the Juju GUI that you just deployed previously. Then Create a Connection between them and expose RestComm to the public.

##2. Manual way - Deploying MySQL and RestComm Charms
# Deploying the charms 


    #boostrap Juju environment
    juju bootstrap
    #get logs
    juju debug-log
    # deploy juju gui
    juju deploy juju-gui
    #expose juju-gui for public access
    juju expose juju-gui

#Deploying RestComm Charm

    #deploy backend DB
    juju deploy mysql
    #if you use juju local (ie lxc - https://jujucharms.com/docs/stable/config-local) as environment mysql needs this below
    #juju set mysql dataset-size='512M'
    #juju resolved -r mysql/#
    #deploy Mobicents RestComm Unit
    juju deploy cs:~jean-deruelle/trusty/mobicents-restcomm-charm
    #connect RestComm to the backend DB
    juju add-relation mobicents-restcomm mysql
    juju expose mobicents-restcomm

#Test RestComm Charm

Go to http://<public_ip>:8080 or http://<public_ip>:8080/restcomm-management (username: administrator@company.com, password: RestComm) for Admininstration

Go to http://<public_ip>:8080/olympus for WebRTC P2P Live Video chat
