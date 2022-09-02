### Requirements
- [Enable Dev Hub in your Org](https://www.youtube.com/watch?v=Y1pZ9sFcILo)
- [Install Salesforce CLI](https://developer.salesforce.com/tools/sfdxcli)
- [Install Git](https://git-scm.com/downloads)
- [Install Fork](https://git-fork.com/)
- [Install Visual Studio Code](https://code.visualstudio.com/download)
- [Set Up Visual Studio Code](https://trailhead.salesforce.com/content/learn/projects/quick-start-lightning-web-components/set-up-visual-studio-code)


  <img width="433" alt="Screenshot 2022-09-01 at 15 47 28" src="https://user-images.githubusercontent.com/89274213/187930087-7d972655-3e41-41aa-88f4-b7307ef94578.png">

1. Clone this repository:
   ```
    git clone https://github.com/campforce/auto-parts-retail.git
    cd auto-parts-retail
   ```
1. Authorize your hub org:

    ```
    sfdx auth:web:login -d -a devhub
    ```

1. Create a scratch org:

    ```
    sfdx force:org:create -s -f config/project-scratch-def.json -a app
    ```

1. Push the app to your scratch org:

    ```
    sfdx force:source:push
    ```
1. Import Sample Data
    ```
    sfdx force:data:tree:import --plan data/data-plan.json
    ```    
1. Open the scratch org:

    ```
    sfdx force:org:open
    ```
