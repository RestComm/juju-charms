Juju Restcomm MySQL Bundle

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


#Deploying RestComm - All Integrated Bundle
Import this bundle through the Juju GUI that you just deployed previously by browsing the Charm Store or importing the bundle.yaml file

#Test RestComm Charm

Go to http://public_ip:8080/restcomm-management or http://public_ip:8080/restcomm-management (username: administrator@company.com, password: RestComm) for Admininstration

## WebRTC call

Go to http://public_ip:8080/olympus for WebRTC P2P Live Video chat

Please refer to this link: http://caniuse.com/#search=webrtc  for the most up-to-date information about browser WebRTC support.

## Clean enviroment  
When you done, you can clean ennviroment and destroy all services (do not terminate machines). 

    juju-deployer -D 
