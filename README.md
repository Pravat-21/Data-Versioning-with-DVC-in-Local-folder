# **Step-by-step process of versioning data with DVC & Local folder:**

- **step-1:**
    - Suppose we want to do a project. so I assume that we create all the necessary folders & files with help of `coockiecutter` template and of course created a virtual environment (although it is not mandetory but it's a good practice to do.)
    - Now assume that we are in that project folder with in virtual environment.

- **step-2:**
    - Do a inital commit after initialized with `GIT` & `DVC`.(assuming that dvc is already installed & git it configured.)
    - If DVC is not installed then-
        ```
        pip install dvc
        ```
    - otherwise initialize with the project folder
        ```
        git init
        ``` 
        ```
        dvc init
        ```
    - then do the following--
        ```
        git add .
        git commit -m "your inital commit"
        git branch -M main
        git remote add origin <your git repo address>
        git push -u origin main
        ```
- **step-3:**
    - Write your code & test it by using-
        ```
        python yourfile_name.py
        ```
    - Here in first version of code I have droped `state_province`,`country`; these two columns.
    - Now it's time to add remote location for data versioning.

    - **STEPS FOR DOING THE DATA VERSIONING IN LOCAL FOLDER:** 
       - Here we create one folder in our `TEMP` directory in order to find out the path run this command in command prompt -
            ```
            echo %TEMP%
            ```
            It will return the path of our `TEMP` folder in our local machine (windows).

        - Then copy the following command into our project terminal
            ```
            dvc remote add -d <TEMP folder path>\new_folder_name
            ```

        - After connecting with `local folder`check about DVC --
            ```
            dvc status
            ```
        - then tracked those file with DVC which we want to (here only data folder will be tracked)
            ```
            dvc add data/
            ```
        - After dvc commit we can push all the files to git & data to our remote location
            
            ```
            git add .
            git commit -m "your commit 2"
            dvc push 
            git push
            ```
            
**First version of the code & data has been successfully tracked.**

---------------------------------------------------------------------------------------------------------------
### Creating the second version of the code & data:
- **step-1:**
    - write your second version of code.
    - Test it again.
    - Now we need again do code & data versioning in the same manner
        ```
        dvc status
        dvc add data/
        ```
        ```
        git status
        ```
        It must show that data.dvc has been modified along with other updated files & folders.

        ```
        git add .
        git commit -m "your commit for second version of code"
        dvc push
        git push
        ```
**Second version of the code & data has been successfully tracked.**

---------------------------------------------------------------------------------------------------------------
## **Now it's the time to check**
- Suppose we want to go the previous version of the project. To do that --
    ```
    git log --oneline
    ```
    It will show all the commits.
- then we can do -
    ```
    git checkout <your commit id for that version of codes>
    ```
    Here we can observe that although the code of this version has been updated but the data is yet to update. In order to fetch data run
    ```
    dvc checkout
    ```
## **And that's how we can do the data versioning with `DVC`& `Local folder`.**

___________________________________________________________________________________
# **Thank You.**
    




       


    
    

