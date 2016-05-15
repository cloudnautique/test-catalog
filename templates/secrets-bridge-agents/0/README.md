## Secrets Bridge Agents (Experimental)
---
###Status: Experimental POC (Read: Do NOT use for production) 
Only works in Dev mode with Hashicorp Vault server in the 0.0.1 release.

---
#### Description: 
  This is the agent component for the Vault secrets bridge with Rancher. This service will be deployed in the environment running applications that need secrets. This service does not have direct access to Vault, it communicates with the Secrets Bridge server.
  
#### Pre-reqs:

An instance of Secrets Bridge server running.

#### Running this app
As services come up, this service will send events to the Secrets Bridge. The server will (Not currently enforced) verify the signed token with Rancher server and get the launching containers Rancher environment, stack, service and Docker ID. With that information the Secrets Bridge server will check with Vault in the `configPath/environment/stack/service/container_name` for a key called policies. It checks from most specific and recursively looks down to the environment key. It uses the most specific match. 

