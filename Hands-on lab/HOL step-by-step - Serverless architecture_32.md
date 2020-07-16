### Task 1: Add git repository to your Visual Studio solution and deploy to GitHub

1. Open the **TollBooth** project in Visual Studio.

2. Right-click the **TollBooth** solution in Solution Explorer, then select **Add Solution to Source Control**.

    ![In Solution Explorer, TollBooth solution is selected. From its right-click context menu, the Add Solution to Source Control item is selected.](media/vs-add-to-source-control.png 'Solution Explorer')

3. Select **View** in Visual Studio's top menu, then select **Team Explorer**.

    ![The View menu is expanded with the Team Explorer menu item selected.](media/vs-view-team-explorer.png 'Visual Studio')

4. Select **Sync** in the Team Explorer.

    ![The Sync link is highlighted.](media/vs-sync.png "Changes")

5. Choose the **Publish to GitHub** button, then sign in to your GitHub account when prompted.

    ![The Publish to GitHub button is highlighted in the Publish to GitHub section.](media/vs-publish-to-github.png "Push")

6. Type in a name for the new GitHub repository, then select **Publish**. This will create the new GitHub repository, add it as a remote to your local git repo, then publish your new commit.

    ![In the Push form, the repository name is highlighted along with the Publish button.](media/vs-publish-to-new-github.png "Push")

7. Refresh your GitHub repository page in your browser. You should see that the project files have been added. Navigate to the **TollBooth** folder of your repo. Notice that the local.settings.json file has not been uploaded. That's because the .gitignore file of the TollBooth project explicitly excludes that file from the repository, making sure you don't accidentally share your application secrets.

    ![On the GitHub Repository webpage for serverless-architecture-lab, on the Code tab, the project files are displayed.](media/github-repo-page.png 'GitHub Repository page')

