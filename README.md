# Abstract

Reproducibility of data is crucial to science. Ease of reproducibility has numerous advantages and there are two very useful tools to aid with this. Galaxy is a workflow manager that ties together and manages the tools and scripts you use to process and analyse data. Docker is a powerful tool that you can use to encapsulate and isolate the runtime environments of your tools from the varied system environments they may face. With the ever growing scale of the datasets being processed, utilising large scale cloud computing is an economical option to generate results faster. Here we will discuss the various features of these tools and how to integrate them together on Amazon Cloud computing systems. We will also demonstrate how to integrate any tool or script that is not already available through Galaxy.

# Preamble

Reproducibility is a core tenet of science. If others are not able to reproduce your findings then it invalidates any conclusions you may have made. This holds true in computational biology where the transformation of raw data into something analysable can be difficult to reproduce. A wide variation in computing environments and runtime parameters needs to be documented or constrained to ensure that any of these factors can be reproduced when transforming the data. To add to the complexity of this task, biological data is relatively large and requires a significant amount of computing power to process the data in a reasonable amount of time. Luckily there are numerous services available that allow you to rent large clusters of computers and set them to your own tasks. The systems that make up these clusters can significantly vary and steps need to be taken to insulate your work from them. 
Utilising tools that make reproducibility easier does more than bolster the credibility of your work, it also makes it easier for others to utilise your work for their own purposes. The next person that want to use your work will also most likely be your future self. If after you have finalised publication and set the work aside forgetting about it, coming back to it later with a new purpose will be significantly easier if you take steps now to ensure ease of reproducibility. Even your current self will be rewarded by the extra effort taken. If erroneous results come up after a significant amount of time and effort was spent, then it will be much easier to iterate on the data while troubleshooting. 
If you have any experience in the data sciences then you will know the tribulations of trying to install and configure all the necessary tools to process data. This is especially true when trying to follow a publication’s vague description of how they generated their results. Wouldn’t it have been nice if the authors had published their entire computing environment? With all the software nicely compiled and all the configuration options already set up? This is entirely possible with a couple pieces of software that we will now discuss.

# Workflow Managers

Let's begin with the idea of a workflow. A workflow is a series of tools and dataset actions that run in sequence to transform data into a useful form. It usually involves data conversion, filtration, transformation, aggregation, segmentation, processing, and visualisation. They can include a mixture of custom scripts, 3rd party software, and manual curation. A workflow manager is a piece of software that keeps track of and executes each step. The two most critical pieces of information that a workflow manager should keep track of is the software version of the tools and the input parameters.
Here is a non-comprehensive list of workflow managers available from [wikipedia](https://en.wikipedia.org/wiki/Bioinformatics_workflow_management_system):
  * Galaxy: Web based graphical workflow manager
  * GenePattern: Web based workflow manager
  * BioBIKE: Web-based, programmable, integrated biological knowledge base.
  * Anduril: Workflow is described in a proprietary scripting language, AndurilScript.

When deciding on a workflow manager, there is a number of secondary qualities you should consider: ease of use, community support, extensibility, and extensive support for available tools. While BioBIKE may meet some specific use cases, it is not well suited for general tasks compared to the other options. Anduril has a steep learning curve and dependency on third party tools to get started. GenePattern and Galaxy are the two main contenders for general use. The defining quality that sets Galaxy apart from GenePattern is its graphical visualisation of the workflow. This makes it very easy and intuitive to get started with Galaxy with minimal training.

# Galaxy Workflow

<a href="images/welcometogalaxy.png"><img src="images/welcometogalaxy.png" class="screenshot" /></a>
This is the first thing you will see when accessing a Galaxy instance. From just this image you can see that it has features supporting multiple users. You can share data and workflows to collaborate with colleagues while keeping everything in one place. Galaxy has a large repository of tools already integrated and many more are available to be easily downloaded and installed from its online “Tool Shed”. On the right you can see it keeps record of everything you do so that you can manually experiment on your data rather than having to predefine a workflow.
Once you have determined the steps, you can formalise the process into a workflow. Galaxy makes this easy with an intuitive drag and drop interface.

<a href="images/HIV_workflow.png"><img src="images/HIV_workflow.png" class="screenshot" /></a>
This is a trivial example of a workflow that uses the T-Coffee multiple sequence aligner to align some input data. The input placeholder was added along with the T-Coffee tool by selecting them from the toolbar on the left. The output of the input placeholder was then simply dragged to the input of T-Coffee to create the mapping. These workflows can be as complex or as simple as needed with a varying number of tools.

The best way to learn is by doing, so let's get you started with your own Galaxy instance.



# Amazon Web Services

<a href="images/AWS/AWS1.jpg"><img src="images/AWS/AWS1.jpg" class="screenshot" /></a>
To sign up for AWS, first open the Amazon web services website [here](https://aws.amazon.com/) and click on “Complete Sign Up”.

<a href="images/AWS/AWS2.jpg"><img src="images/AWS/AWS2.jpg" class="screenshot" /></a>
Click on “Create a new AWS account”. If you already have an AWS account, skip to 11.

<a href="images/AWS/AWS3.jpg"><img src="images/AWS/AWS3.jpg" class="screenshot" /></a>
Enter your email address, password, and a AWS account name. Then, click on “Continue”.

<a href="images/AWS/AWS4.jpg"><img src="images/AWS/AWS4.jpg" class="screenshot" /></a>
A page will then show up to choose the account type you want to create. Select “Professional” if you want it for a company, an educational institution, or organisation, otherwise select “Personal”. Then, fill in your information and click on “Create Account and Continue”.

<a href="images/AWS/AWS5.jpg"><img src="images/AWS/AWS5.jpg" class="screenshot" /></a>
Now, enter your payment information and click on “Secure Submit”.

<a href="images/AWS/AWS6.jpg"><img src="images/AWS/AWS6.jpg" class="screenshot" /></a>
Then, verify your phone number by clicking on “Call Me Now”.

<a href="images/AWS/AWS7.jpg"><img src="images/AWS/AWS7.jpg" class="screenshot" /></a>
Wait for the call and enter the 4-digit code that is displayed and your identity should be verified.

<a href="images/AWS/AWS8.jpg"><img src="images/AWS/AWS8.jpg" class="screenshot" /></a>
Click on “Free” to select “Basic Plan”.

<a href="images/AWS/AWS9.jpg"><img src="images/AWS/AWS9.jpg" class="screenshot" /></a>
You can add more details to personalize your experience if you want to.

<a href="images/AWS/AWS10.jpg"><img src="images/AWS/AWS10.jpg" class="screenshot" /></a>
Now, to create an access key, first click on “Sign In to the Console”.

<a href="images/AWS/AWS11.jpg"><img src="images/AWS/AWS11.jpg" class="screenshot" /></a>
Sign in by using the account you just created.

<a href="images/AWS/AWS12.jpg"><img src="images/AWS/AWS12.jpg" class="screenshot" /></a>
Then, click on “My Security Credentials” under your account name.

<a href="images/AWS/AWS13.jpg"><img src="images/AWS/AWS13.jpg" class="screenshot" /></a>
Click on “Continue to Security Credentials”.

<a href="images/AWS/AWS14.jpg"><img src="images/AWS/AWS14.jpg" class="screenshot" /></a>
Click on “Users” in the left sidebar.

<a href="images/AWS/AWS15.jpg"><img src="images/AWS/AWS15.jpg" class="screenshot" /></a>
If there are no users, click on “Add user”. If there is a user, go to 20.

<a href="images/AWS/AWS16.jpg"><img src="images/AWS/AWS16.jpg" class="screenshot" /></a>
Fill in the information and click on “Next: Permissions”.

<a href="images/AWS/AWS17.jpg"><img src="images/AWS/AWS17.jpg" class="screenshot" /></a>
Click on “Next: Review”.

<a href="images/AWS/AWS18.jpg"><img src="images/AWS/AWS18.jpg" class="screenshot" /></a>
Click on “Create user”.

<a href="images/AWS/AWS19.jpg"><img src="images/AWS/AWS19.jpg" class="screenshot" /></a>
Click on “Close”.

<a href="images/AWS/AWS20.jpg"><img src="images/AWS/AWS20.jpg" class="screenshot" /></a>
Now, click on the user you just created.

<a href="images/AWS/AWS21.jpg"><img src="images/AWS/AWS21.jpg" class="screenshot" /></a>
Then, click on the “Security credentials” tab.

<a href="images/AWS/AWS22.jpg"><img src="images/AWS/AWS22.jpg" class="screenshot" /></a>
Click on “Create access key”.

<a href="images/AWS/AWS23.jpg"><img src="images/AWS/AWS23.jpg" class="screenshot" /></a>
Click on “Download .csv file” to save the access key ID and secret access key to a CSV file on your computer. Store the file in a secure location. You will not have access to the secret access key again after this dialog box closes. After you have downloaded the CSV file, choose “Close”.

In case you need more information about access keys, click [here](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html).

# Cloudman

Once you have an account with AWS and an access key ready, you can begin with launching an instance of Galaxy on their systems. One of Galaxy’s many features is the accompanying CloudMan project that removes all the guesswork of installing and configuring a complete instance. It is a relatively painless process, even for someone with zero experience with Galaxy or AWS.
To begin, open the cloudman launcher [here](https://beta.launch.usegalaxy.org/).

<a href="images/cloudman.png"><img src="images/cloudman.png" class="screenshot" /></a>
CloudMan manages your past and running Galaxy instances and so it needs a means of identifying you. Click the “Login” menu option in the top right.

<a href="images/cloudman_login.png"><img src="images/cloudman_login.png" class="screenshot" /></a>
It will identify you through an account you have with one of the listed services. Click the preferred service you would like to use.

<a href="images/cloudman_catalog.png"><img src="images/cloudman_catalog.png" class="screenshot" /></a>
Once you have logged in, scroll down the catalog list and select the Galaxy CloudMan appliance.

<a href="images/cloudman_launch.png"><img src="images/cloudman_launch.png" class="screenshot" /></a>
This will prompt you for the access key you generated in the previous section. You will have to open the file with a text editor and copy out the access key ID and secret key as the format expected by the “Load credentials from file” option is not compatible with the file given to you by Amazon. For the purpose of this tutorial you should also have ‘Amazon US East 1 - N. Virginia’ selected. Some Amazon Clouds are not currently supported by CloudMan. Once you have entered the information, click the “Test and use these credentials” button. You also have the option to click the “Save to Profile“ button to save the credentials for future use. When ready click “Next”.

<a href="images/cloudman_launch2.png"><img src="images/cloudman_launch2.png" class="screenshot" /></a>
The next prompt asks you the specifics of the computer you want to run your root node on.
One important gotcha that we ran into when producing this tutorial is that Galaxy requires a significant amount of RAM and disk space. 50Gb is a safe number to allocate leaving lots of room for uploading your data. It is also important that you select “m4.xlarge” for the hardware as the Galaxy installation process requires a large amount of RAM and will fail if not allocated enough. This means you can’t use the lower free tiers that AWS offers for your primary node. It is important that you remember the password you enter here as you will use it throughout this tutorial. Once you are ready, click “Next”.

<a href="images/cloudman_launched.png"><img src="images/cloudman_launched.png" class="screenshot" /></a>
This will access AWS and automatically install and configure Galaxy.
It is also important to take note of the IP address here as it will be used later in this tutorial. In the image it is ‘34.201.1.85’ but will be different for your instance. Once you have recorded the address, wait for the status to say ‘Running’ and click the link to open the CloudMan manager page for your running instance.

<a href="images/cloud_login.png"><img src="images/cloud_login.png" class="screenshot" /></a>
It will ask you to authenticate, use ‘ubuntu’ as the username and the password you specified when creating the instance.

<a href="images/cloudman_init.png"><img src="images/cloudman_init.png" class="screenshot" /></a>
Take note of the two green circles on the “Service Status” line. You need to wait for both to be green before you can continue. Once they are green, close the message box at the top. This page allows you to manage the cluster that was configured for you by CloudMan. While not necessary for this tutorial, you can increase the number of worker nodes allocated or turn on auto scaling which will grow and shrink the cluster as needed. Be careful with that feature though as it could cause you to receive a very large bill from AWS if it allocated a large number of nodes for a job.

<a href="images/cloudman_admin.png"><img src="images/cloudman_admin.png" class="screenshot" /></a>
In order to download tools from the tool shed, you need to become an admin user of the galaxy instance.
To do so, click on the “Admin” section on the top right corner of the page and type your email address in the box highlighted. Once entered click the “Set admin users” button.
Once that is done, click on the CloudMan icon in the top left corner of the page to return to the main page. Wait again for the circles to be green on the “Service Status” line. When they are green, click the “Access Galaxy” button.

# Install a Galaxy tool from the ToolShed

<a href="images/galaxy_register.png"><img src="images/galaxy_register.png" class="screenshot" /></a>
The first thing you need to do is register yourself using the email address you entered into the CloudMan admin page. Click “Login or Register” and fill out the form.

<a href="images/galaxy_toolshed.png"><img src="images/galaxy_toolshed.png" class="screenshot" /></a>
If everything went well and you used the same email as entered in the previous section then you should be provided with a “Admin” menu option on the top bar. Click on it, then click on “Search Tool Shed” under “Tools and Tool Shed” on the sidebar on the left. Select “Galaxy Main Tool Shed” in the options presented. If it prompts, select “Browse valid repositories”.

<a href="images/galaxy_toolshed_search.png"><img src="images/galaxy_toolshed_search.png" class="screenshot" /></a>
In the search box provided search for ‘coffee’. This will provide a list of matching tools from the main Galaxy tool repository. For this tutorial we will use the one owned by ‘ayllon’. Click the corresponding button and click “Preview and install”.

<a href="images/galaxy_tcoffee_install.png"><img src="images/galaxy_tcoffee_install.png" class="screenshot" /></a>
Click the “Install to Galaxy” button at the top.

<a href="images/galaxy_tcoffee_install2.png"><img src="images/galaxy_tcoffee_install2.png" class="screenshot" /></a>
It gives you the option to specify the category that the tools is listed on the left toolbar when doing analysis or building a workflow. You can specify a new one or select an existing one. Select “Multiple Alignments” from the drop down box and click “Install”.

<a href="images/galaxy_tcoffee_installed.png"><img src="images/galaxy_tcoffee_installed.png" class="screenshot" /></a>
When the installation is complete you should see the green “Installed” status on the right.

<a href="images/galaxy_new_workflow.png"><img src="images/galaxy_new_workflow.png" class="screenshot" /></a>
Next we will test the tool in a workflow. Click the Workflow option on the top toolbar and click the “Create new workflow” button that is shown. 

<a href="images/galaxy_name_workflow.png"><img src="images/galaxy_name_workflow.png" class="screenshot" /></a>
Enter a descriptive name and possibly a longer description in the respective fields and click “Create”.

<a href="images/galaxy_inputdata.png"><img src="images/galaxy_inputdata.png" class="screenshot" /></a>
In the workflow editor, select the “Inputs” category on the left and add a “Input dataset” placeholder to the workflow.

<a href="images/galaxy_tcoffee_workflow.png"><img src="images/galaxy_tcoffee_workflow.png" class="screenshot" /></a>
Then use the search box at the top of the toolbox to search for ‘coffee’, this will reduce the list to any matches. Add the T-Coffee aligner tool the same way you did the Input dataset placeholder. Now drag the small arrow to the right of ‘output’ on the Input dataset placeholder. This will create a line you can then drag to the input arrow on the left of ‘Source File’ for the T-Coffee placeholder.
Click the T-Coffee placeholder box so that the T-Coffee options appear on the right. Check ‘kalign_msa’ and ‘Yes’ under the clustalw_aln output option.
One kwirk about Galaxy is that many of its important menu functions are unlabelled icons just below the top menu bar. If you are looking for a menu option it is best to start looking there. If you hover your mouse over the gear icon at the top it should pop up with a description. Click the gear icon and select “Save”. Click the gear icon again and select “Close”.

<a href="images/galaxy_tcoffee_workflow_run.png"><img src="images/galaxy_tcoffee_workflow_run.png" class="screenshot" /></a>
Now that you have your workflow setup you can test everything by running it. Your workflow is now listed under the “Workflow” menu option. Click the button for the workflow you created and select “Run”.

<a href="images/galaxy_get_data.png"><img src="images/galaxy_get_data.png" class="screenshot" /></a>
Now is a good time to upload some test data. We have prepared a small dataset that will align well, you can download it here. It is 20 HIV genomes taken from the HIV Sequence Database hosted by Los Alamos National Laboratories.
Click “Upload File” under the “Get Data” category on the left.

<a href="images/upload_data.png"><img src="images/upload_data.png" class="screenshot" /></a>
This will present you with a upload box that you can then drag the test data file into or click “Choose local file” to select the file. Once selected click “Start”, wait for the upload to finish and then click “Close”.

<a href="images/run_workflow.png"><img src="images/run_workflow.png" class="screenshot" /></a>
If the input dataset dropdown doesn’t automatically switch to the uploaded file then refresh the page.
Pay attention to the history on the right, it keeps track of everything you did and you can then later download it for your record. It also contains all the uploaded data and results from your analysis. With the correct data set selected in the “Input dataset” drop down click “Run workflow” at the top.

<a href="images/run_workflow_result.png"><img src="images/run_workflow_result.png" class="screenshot" /></a>
The workflow task will appear in the History on the right as a greyed out box. Wait until it turns green signifying that the computation is complete. You can then click on the task to expand its options, this provides a download icon that allows you to download the resulting alignment file. Back in the “Workflow” section you also have the option to download the workflow that you created so that you can send it to others and they can import it into their Galaxy instances.
The best way to familiarise yourself with Galaxy is to play with its many tools and functions. The developers put in significant effort to ensure that someone can’t do any harm to the system from Galaxy, so you don’t have to worry when experimenting with the various features.

