# macOS 10.n.n Fleet Management - k8s Helm Chart
#### Includes: Munki-repo, MacAdmins SAL Reporing, and embedded PostgreSQL Database .    

What's this for?
This is a solution for macOS based workstation/laptop fleet configuration and patch management

#### Installation      
(must be done in this order)
1. install the PostgreSQL chart   
```bash
$ helm install --namespace wksmgmt --name sal-postgresql \
  --set postgresUser=saldbuser,postgresPassword=someAwesomePassword,postgresDatabase=saldb postgresq
```
1. install MUNKI chart + Configure the default site and repository    
```bash
$ helm install --namespace wksmgmt --name munki munki
```
1. install SAL chart   
```bash
$ helm install --namespace wksmgmt --name sal sal
```

The design is based on the guidance provided by MacAdmins [macadmins.psu.edu](http://macadmins.psu.edu/)      
and Google MacOps teams: [google/macops](https://github.com/google/macops)       
*SAL OpenSource*: [salopensource/sal](https://github.com/salopensource/sal)     
![Sal Dashboard](./docs/sal.png)     

*Munki*: [munki](https://www.munki.org/)         
![Sal Dashboard](./docs/munki.png)    


Remote storage: mount remote Munki pacakge site via fuse-sshfs      
*FuseSSHFS*: [libfuse/sshfs](https://github.com/libfuse/sshfs)       

Leverage AutoPackager to manage recipies:    
*autopkgr*: [lindegroup/autopkgr](https://github.com/lindegroup/autopkgr)      
![AutoPkgR](./docs/autopkgr.png)    

Use MunkiAdmin to manage remote Munki Repository        
*MunkiAdmin* [hjuutilainen/munkiadmin](https://github.com/hjuutilainen/munkiadmin)       

The entire solution (With the exception of the management tools) can be deployed on a Kubernetes Cluster:     
![Design](./docs/munki-design.png)      


*//TODO*     
- Leverage CICD & job sceduling to automate packaging

2018 gjyoung1974@gmail.com
---

