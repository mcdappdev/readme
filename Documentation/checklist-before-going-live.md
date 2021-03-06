# Checklist before going live with a project

When a project is ready to be deployed and go live, there's a couple of things one needs to remember to have in place - this is good place to start, although it might not cover everything for your project.

## What to check before going live

- **Redis**: Check that the provider has been added and Redis is being used for sessions in `droplet.json`. Also make sure that the sessions middleware has been added.
- **Bugsnag**: Make sure that the project has been created (on Bugsnag) and the correct credentials has been added to all environments using environment variables. Make sure that the Bugsnag middleware has been added and consider doing a simple test to see if errors are being reported correctly.
- **Meta**: Check that the middleware has been added and it is being enforced when doing requests.
- **Crypto**: Check that the keys for hashers and ciphers has been generated correctly. Consider if it is needed to move the keys to environment variables to ensure that generated tokens cannot be used across different environments.
- **SSO**: If your project includes an admin panel, then make sure to add Nodes SSO as well. Remember to create credentials for the project and make sure that they are added to all environments as environment variables.
- **Storage**: If file uploads are supported, make sure that the Storage credentials has been correctly added to all environments as environment variables.
- **Mail**: If your project supports sending mails, make sure all mail related credentials has been setup correctly as environment variables on all environments.
- **CORS**: The default Nodes template comes with the CORS middleware installed and configured. Consider whether or not you need to limit the domains and/or remove from or add to the list of allowed headers.
- **Continuous Integration**: Is your repo on GitHub running correctly with Circle CI? Is your master/develop branches protected?
- **Debug logs**: If you have debug logs turned on (e.g. in `fluent.json`) while developing the project, consider turning them off before deploying.
- **Signers**: Are you using JWT and will be running the project on multiple environments? If so, remember to generate keys for each environment. Consider adding the keys as different config files (opposed to environment variables).
