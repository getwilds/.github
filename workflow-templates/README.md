## Pull Request Deploy Previews

Pre-requisites

- Install Netlify cli tool
	- macos: use homebrew: `homebrew install netlify-cli`
	- other platforms: see <https://docs.netlify.com/cli/get-started/>
- Install GitHub cli tool
	- see <https://cli.github.com/>

1. Netlify (CLI)
	- inside your project
	- login to Netlify: `netlify login`
	- Initialize your project with Netlify: `netlify init` 
	- Remove git integration so site only builds when we tell it to
		- Run `netlify open` to go the Netlify page for the app
		- Site Configuration > Build & Deploy > Unlink github repo

2. In your GitHub repository (CLI)
	- Add the token as an env var as `NETLIFY_AUTH_TOKEN` to your repo
		- Run `gh secret set NETLIFY_AUTH_TOKEN -a actions -b <your token>`
	- Permissions changes
		- (workflow permissions need to be changed, but they should be set correctly for all WILDS repos by default)

3. Setup the workflow file (Browser)
	- Go to the actions tab of your repo
	- Click "New workflow"
	- Click "Quarto Deploy Preview" (see [starter workflows](https://docs.github.com/en/actions/using-workflows/creating-starter-workflows-for-your-organization) for reference)
	- In the file that opens up set the NETLIFY_SITE_ID to the site id in the Configuration page of your Netlify app
	- Commit the GH action file

You're done!

Upon the next pull request, you should see a ping back from Netlify:

![screenshot of deploy preview in a pull request](deploy-preview.png)
