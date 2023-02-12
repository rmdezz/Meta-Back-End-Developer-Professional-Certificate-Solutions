# Organizing an API Project

# Introduction

- Importance of upfront planning and organizing for a project to be maintainable
- Splitting a big app into multiple apps to make sure that all goals are met
- Decoupling the apps to deal with a particular set of relevant problems
- Prevention of a production block due to unmanageable app

# Dependencies management

- Use of virtual environment instead of global environment for project dependencies
- Avoiding conflicts with packages by using a virtual environment
- Saving packages and their version numbers in a separate requirements.txt file
- Use of pipenv for easier dependency management

# API Upgrades

- Use of versioning for API upgrades
- Launching updated version after keeping the old working API intact
- Creation of separate app for newer version instead of adding everything in the old app

# Resource Management

- Separate resource folders for each app to avoid conflicts and efficiently manage files
- Keeping app-specific static files inside the app itself
- Splitting relevant settings into separate files and including them all from the main settings
- Use of Django splits settings to manage settings

# Bussiness Logic and Models

- Placing all the business logic interviews in related models
- Writing manageable code and organizing necessary pieces in one place
- Making models more powerful, decoupled, and reusable

# Summary

- Keeping the project organized for better productivity, reusability, and easier deployments
- Crucial points to keep the project manageable over time
- Splitting the app into multiple apps, using a virtual environment, API upgrades, resource management, and business logic and models.