import scratchattach as sa
import json

session = sa.login("Dagriffpatchfan", "the_pw")
cloud = session.connect_cloud("1110802552") #replace with your project id
client = cloud.requests()

@client.request
def agent(argument1): #called when client receives request
    print(f"User: {argument1}")
    user = session.connect_user(argument1)
    project = user.projects(limit=3, offset=0)[0]
    print (f"Project URL: {project.url}")
    agent = project.raw_json().get('meta', {}).get('agent')
    print(f"Agent: {agent}")
    return agent

@client.event
def on_ready():
    print("Request handler is running")

client.start(thread=True) # thread=True is an optional argument. It makes the cloud requests handler run in a thread
