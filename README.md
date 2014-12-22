GEOG 410/510 Lab Assignments
============================
for GEOG 410/510: Advanced GIS Programming taught winter 2015 at Portland State University


**Overview**

The six subfolders of this repo contain the data and instructions of the six lab assignments for GEOG 410/510. Each assignment's instructions are in each subfolder's README.md. Questions and/or issues can be added to the issue tracker for this repo.


**I am a student. How do I access these assignments?**

One possible way to get the assignments is to download the whole repository as a zip file using the github interface. However, as all the labs folders are in the same repo, labs assigned later in the term may not yet be pushed to the repo when it is first downloaded, and the whole repo will need to be re-downloaded once those labs are available. I do not recommend this method if one has git available.

A better way: use git to clone the repo locally. Thus, one can use `git clone <repo url>` to copy down all the files to his or her local machine. One can work within each lab folder in this clone; files will not be updated after the start date for each assignment as listed on the course schedule. Before beginning the next lab, a student can ensure he or she has all of the lastest files by using the `git pull` command. This command will fetch any updates in the upstream repository (the github repo), and try to perform a fast-forward merge (e.g., the user does not need to work out any merge conflicts). As no files will be updated in labs that have already started, a fast-forward merge should happen every time.


**Submitting these assignments**

Submit completed lab assignments on D2L, following the submission requirements in the lab's instructions. If submitting multiple files, please zip them together. Name the zipfile or any single files as “lastnameFirstname_assignment#”. For example, if I were submitting lab 5, I would zip all my submitted files together and name the zip file “keiferJarrett_lab5.zip”. Failure to follow the proper naming convention will result in lost points.

Another way to submit assignments is to use git and github. A student can do this one of two ways: (1) fork the 410Labs repo, renaming is as 410Lab#, where # is the lab number; or (2) create a blank repo named 410Lab#, where # is the lab number, and put all the lab files in that repo. In either case, to complete the submission to me, add jkeifer as a collaborator on the repository. Keep in mind that commit history is public: I will be able to see grade a submission as it was on the due date, even if changes have been made since. BUT PLEASE, do not make changes after the due date even so.
