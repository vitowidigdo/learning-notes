FROM node:19-alpine3.17
COPY . /app
WORKDIR /app
# So that every run is sleep and you just have to add seconds 
ENTRYPOINT [ "sleep" ]
CMD ["node app.js;10"]

# You can easily override this command
# CMD [ "10" ]