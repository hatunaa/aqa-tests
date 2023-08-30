# Overview 

The jck_target_folder_check.sh script is used to cross-check if all second-level JCK folders in a given JCK repo have their corresponding playlist targets under https://github.com/adoptium/aqa-tests/tree/master/jck


# How to run the script locally 


```

- Checkout `jck_target_folder_check.sh to your local machine from https://github.com/adoptium/aqa-tests/tree/master/jck
- Manually download/unpack the SDK you want to use at {someLocation}
- export TEST_JDK_HOME={someLocation} (path to java/bin folder)
- git clone https://github.com/adoptium/aqa-tests.git at {WorkspaceLocation}
- cd /{WorkspaceLocation}/aqa-tests
- ./get.sh //This will checkout TKG under /{WorkspaceLocation}/aqa-tests
- Run jck_target_folder_check.sh {jck-repo-name} {WorkspaceLocation}
```
Sample input to run script
```
$ jck_target_folder_check.sh git@github.ibm.com:runtimes/JCK21-unzipped.git <LOCAL_AQA_TESTS_REPO>
```

# What the script does 


```
1. Git clone the the given JCK repo (if they do not already exist under given {WorkspaceLocation}).
2. Run TKG to generate out the full list of playlist targets applicable to the JDK version of the SDK being used (e.g. the one at `TEST_JDK_HOME`). 
3. Use `find` command to generate the list of second level folders available under the main test directories of the downloaded JCK repo.  
4. Clean up the generated lists and cross check them to flush out cases where we have test folders in the repo but do not have corresponding targets in the playlist 

```

# Prerequisite: 


```
Since this script downloads JCK materials, any SSH keys required to access the given JCK repository needs to be set up on your local environment prior to invoking the script. 

```
