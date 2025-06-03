# Bun Vercel

How to host a Bun-based web application on Vercel.

1. Go to Vercel > Add New > Project
2. Click on Adjust GitHub App Permissions on the Import Git Repository page
3. Click on Configure next to your GitHub account
4. Scroll down to Only Select Repositories and click Select Repositories
5. Locate the new repository and click on the Save button
6. Select the new repository back on the Import Git Repository page
7. Click on Import and select or keep Other in Framework Preset\

   The option will default to Other in case the repository is empty or has no
   existing infrastructure matching what Vercel can recognize.

8. Leave Root Directory at `./` and expand the Build and Output Settings section
9. Leave all those options off - we will configure the run command but not these

   This is because Bun needs to build step and will drop no artifacts, but we're
   showing this to be aware that there is an override option for the run command
   which is not present here.

10. Create `index.ts` in the repository with basic Bun web handler:

    ```typescript

    ```

11. Click the Deploy button and wait, then click on Continue to Dashboard
12. Check the Vercel-provided URL to find right now it serves `index.ts` as-is
13. Go to Settings > Build and Deployment > Development Command
14. Toggle Override on and change the command to `bun .` and click Save
15. Go back to the Deployments tab and click ⋯ > Create Deployment > `main`
16. Confirm with Create Deployment and wait for the deployment to finish

This will keep serving the Bun code as text.

Go back to Settings > Framework Settings and change the selection to Next and
Save.

This will also fail as Next will not be detected and the install and build
commands won't pass.

Go back to Build and Deployment and change the install and build commands to
`true` to make them pass.
I also set Output Directory to `.`.

This still fails as Next is not detected.
Since there is no Node framework setting I assume it is not possible to run Bun
without also bundling Node in the dependencies which is not what I want.
