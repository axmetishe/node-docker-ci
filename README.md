# node-docker-ci
Environment configured via compose. Docker in Docker as described in task is a big security issue for docker host and evil at all, that's why environment deployed with compose already contain app instance and db backend instance, but application is not deployed.

In Jenkins you'll find task which build, run test, prepare native packaging and deploys successfully built application on host via ssh. On app host nginx is used as proxy.
RPM install package files, service file, enable service and reload nginx,

Private repositories on github is non-free that's why I used public repository.

application: https://github.com/axmetishe/meteor-todolist
infrastructure: https://github.com/axmetishe/node-docker-ci
