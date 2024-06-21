# set the base image to create the image for react app
FROM node:20-alpine

# create a user with permission to run app
# -S -> Create a system user
# -G -> add user to grp 
# This is done to abaid running app as root user
# If the app is run by root, any vulnerability is the app can be exploited to gain access to whole system
# It is best practice to run app as nonroot user
RUN addgroup app && adduser -S -G app app

# set the user to run the app
USER app

# set the working directory to /app
WORKDIR /app

COPY package*.json ./

USER root

RUN chown -R app:app .
USER app
RUN npm install
COPY . .

EXPOSE 5173:5173

CMD npm run dev
