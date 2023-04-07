
<p align="center">
    <img width="400" src="https://raw.githubusercontent.com/faan11/koch/master/images/logo.webp" alt="Koch logo">
</p>


# What is Koch 

Koch is a minimal sh script that works around **oc** tool, that is:

- **Fast:** one login and you are ready to go,
- **Simple:** based on lightweight commands such as curl and yq,
- **Secure:** Koch creates temporary token using cli and you don't need anymore service account and the web console to login!, 
- **Configurable:** all clusters are defined in a yaml file similar to other tools,
- **Supported:** Koch supports Openshift® v3.x and 4.x
- **Easy:** quick to install – start using it in minutes.

Authentication can be achieved through:
- **Prompt:** the CLI requests user and password data
- **Bitwarden:** the bitwarden client by looking at user and password in a strongbox entry.

## Installation

### Prerequisites
- sh, used to execute the script.
- [yq](https://github.com/mikefarah/yq), used to manage yaml configuration (tested with v4.33.0)
- [curl](https://github.com/curl/curl), used to request temporary authentication token
- [oc](https://github.com/openshift/oc), used to perform login and logout operation once received the token.
- [bw](https://github.com/bitwarden/clients)  (bitwarden-cli, optional), used to request credentials
- [jq](https://github.com/stedolan/jq) (optional), used to parse credentials json 

### Recommended software
- [starship](https://github.com/starship/starship), used to know the current kubectl context 
- [kubectx](https://github.com/ahmetb/kubectx), to change between kubectl context
- [kubens](https://github.com/ahmetb/kubectx), to change the current namespace
- [fzf](https://github.com/junegunn/fzf) , to properly select the kubernetes context and namespace

### Download and install
This script downloads and install the koch script in the bin directory of the user. You can also install system-wide.
```
curl -o koch https://raw.githubusercontent.com/faan11/koch/1.0.0/koch
mv koch $HOME/.local/bin/
chmod +x $HOME/.local/bin/koch
```
## Usage
You can get the help command by simply typing
```
koch
```

The following command defines a cluster configuration.
```
koch define <context-name> --auth="$AUTH_SERVER" --api="$API_SERVER" --context="$KUBECTL_CONTEXT" --secrethandler="$SECRETHANDLER" --secretname="$SECRETNAME" --insecure="true"
```
where context-name represents the cluster configuration name.  
**$AUTH\_SERVER** represents the scheme and the host used to point out the authentication server ( for instance https://myauthservice.com ).  
**$API\_SERVER** is the scheme and the host of api server used to perform login (for instance, https://apiserver:6443 )

Once the configuration is defined, the user can perform authentication by using the context name.
```
koch login <context-name>
```
This command requests the temporary authentication token and perform authentication using oc login.
```
koch logout
```
Koch logout performs the logout operation.

## How to contribute
Feel free to open an issue in the repo and proposes new ideas.
 
## Contributors
- Fabio Pagnotta <fabio.pagnotta@kiratech.it>
