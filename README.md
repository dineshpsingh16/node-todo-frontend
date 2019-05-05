# node-todo-frontend
This is to demonstrate to jenkins pipeline integration of docker registry with polling of commit in master branch and create new docker image and push to my docker registry account.
# To configure jenkins:
1) Install jenkins
2) Install Blue Ocean plugin
3) Create new pipeline using Blue Ocean plugin
4) Specify gitgub account details
5) Select project node-todo-frontend
# Create docker repo
1) Login to https://hub.docker.com
2) Create todo-repo repository
# Trigger jenkins 
1) Update repo node-todo-frontend
2) after few minutes new image will be pushed in todo-repo with new build id
