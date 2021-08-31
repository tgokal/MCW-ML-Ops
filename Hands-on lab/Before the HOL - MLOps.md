![Microsoft Cloud Workshops](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/main/Media/ms-cloud-workshop.png "Microsoft Cloud Workshops")

<div class="MCWHeader1">
MLOps
</div>

<div class="MCWHeader2">
Before the hands-on lab setup guide
</div>

<div class="MCWHeader3">
September 2021
</div>

Information in this document, including URL and other Internet Web site references, is subject to change without notice. Unless otherwise noted, the example companies, organizations, products, domain names, e-mail addresses, logos, people, places, and events depicted herein are fictitious, and no association with any real company, organization, product, domain name, e-mail address, logo, person, place or event is intended or should be inferred. Complying with all applicable copyright laws is the responsibility of the user. Without limiting the rights under copyright, no part of this document may be reproduced, stored in or introduced into a retrieval system, or transmitted in any form or by any means (electronic, mechanical, photocopying, recording, or otherwise), or for any purpose, without the express written permission of Microsoft Corporation.

Microsoft may have patents, patent applications, trademarks, copyrights, or other intellectual property rights covering subject matter in this document. Except as expressly provided in any written license agreement from Microsoft, the furnishing of this document does not give you any license to these patents, trademarks, copyrights, or other intellectual property.

The names of manufacturers, products, or URLs are provided for informational purposes only and Microsoft makes no representations and warranties, either expressed, implied, or statutory, regarding these manufacturers or the use of the products with any Microsoft technologies. The inclusion of a manufacturer or product does not imply endorsement of Microsoft of the manufacturer or product. Links may be provided to third party sites. Such sites are not under the control of Microsoft and Microsoft is not responsible for the contents of any linked site or any link contained in a linked site, or any changes or updates to such sites. Microsoft is not responsible for webcasting or any other form of transmission received from any linked site. Microsoft is providing these links to you only as a convenience, and the inclusion of any link does not imply endorsement of Microsoft of the site or the products contained therein.

© 2020 Microsoft Corporation. All rights reserved.

Microsoft and the trademarks listed at <https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/Usage/General.aspx> are trademarks of the Microsoft group of companies. All other trademarks are property of their respective owners.

**Contents**

<!-- TOC -->

- [MLOps before the hands-on lab setup guide](#mlops-before-the-hands-on-lab-setup-guide)
  - [Requirements](#requirements)
  - [Before the hands-on lab](#before-the-hands-on-lab)
    - [Task 1: Install the Microsoft DevLabs Machine Learning plugin for Azure DevOps](#task-1-install-the-microsoft-devlabs-machine-learning-plugin-for-azure-devops)
    - [Task 2: Create an Azure Machine Learning workspace](#task-2-create-an-azure-machine-learning-workspace)
    - [Task 3: Setup AKS Cluster for Production Deployment](#Task-3-setup-aks-cluster-for-production-deployment)
    - [Task 4: Setup Azure DevOps Agent](#task-3-setup-azure-devops-agent)

<!-- /TOC -->

# MLOps before the hands-on lab setup guide

## Requirements

1. Azure subscription. You will need a valid and active Azure account to complete the quickstarts. If you do not have one, you can sign up for a [free trial](https://azure.microsoft.com/en-us/free/).

   - The Microsoft Azure subscription must be pay-as-you-go or MSDN.

   - Trial subscriptions will not work. You will run into issues with Azure resource quota limits.

   - Subscriptions with access limited to a single resource group will not work. You will need the ability to deploy multiple resource groups.

2. Azure DevOps subscription. You will need a valid and active Azure DevOps account to complete the quickstarts. If you do not have one, you can sign up for a [free account](https://azure.microsoft.com/en-us/services/devops/).

   > **Note**: You will need privileges to create projects on the DevOps account. Also, you need privileges to create Service Principal in the tenet. This translates to **Ensure that the user has 'Owner' or 'User Access Administrator' permissions on the Subscription**.

3. Azure Machine Learning service workspace. An Azure Machine Learning workspace is a foundational resource in the cloud that you use to experiment, train, and deploy machine learning models. It ties your Azure subscription and resource group to an easily consumed object in the service.

4. Azure Machine Learning compute instance. The compute instance is created during Exercise 1 from the hands-on lab. It used as your fully configured and managed development environment in the cloud to run the quickstart integrated notebooks uploaded in your workspace file share.

## Before the hands-on lab

### Task 1: Install the Microsoft DevLabs Machine Learning plugin for Azure DevOps

1. Navigate to the VisualStudio Marketplace: https://marketplace.visualstudio.com/items?itemName=ms-air-aiagility.vss-services-azureml and select **Get it free**.

2. Select **Azure DevOps organization** from the dropdown list and then select **Install**.

    ![The Microsoft DevLabs Machine Learning plugin for Azure DevOps page is shown with the Azure DevOps organization selected and the Install button highlighted.](media/bhol-04.png 'Install Plug-In')

### Task 2: Create an Azure Machine Learning workspace

1. Sign in to [Azure portal](https://portal.azure.com) by using the credentials for your Azure subscription.

2. In the upper-left corner of Azure portal, select **+ Create a resource**.

3. Use the search bar to find the **Machine Learning**.

4. Select **Machine Learning**.

5. In the **Machine Learning** pane, select **Create** to begin.

   ![The Machine Learning page displays with the Create button selected.](media/bhol-01.png 'Open Create Azure Machine Learning Workspace')

6. Provide the following information to configure your new workspace:

   - **Workspace name**: Enter a unique name that identifies your workspace. In this example, we use **quick-start-ws**. Names must be unique across the resource group. Use a name that's easy to recall and to differentiate from workspaces created by others.

   - **Subscription**: Select the Azure subscription that you want to use.

   - **Resource group**: Use an existing resource group in your subscription or enter a name to create a new resource group. A resource group holds related resources for an Azure solution. In this example, we use **MCW-MLOps**.

   - **Location**: Select the location closest to your users and the data resources to create your workspace.

   - **Workspace edition**: **Basic**. The workspace type (Basic & Enterprise) determines the features to which you’ll have access and pricing. Exercises in this tutorial works on either Basic or Enterprise editions.

   ![The Machine Learning Create form is displayed populated with the aforementioned values. The Review + Create button is highlighted.](media/bhol-02.png 'Create Azure Machine Learning Workspace page')

7. After you are finished configuring the workspace, select **Review + Create**. Select **Create** after you review the fields you just entered.

    > **Note**: It can take several minutes to create your workspace in the cloud.

    When the process is finished, a deployment success message appears.

8. To view the new workspace, select **Go to resource**.

9. Navigate to the [Azure Machine Learning Studio](https://ml.azure.com) and select the workspace that you created or select **Launch now** under **Try the new Azure Machine Learning studio** in the **Overview** section of your Azure Machine Learning workspace.

   ![The Machine Learning resource page is shown with Overview selected from the left menu, and the Launch now button highlighted in the Overview screen.](media/bhol-03.png 'Launch the Azure Machine Learning studio')

### Task 3: Setup AKS Cluster for Production Deployment

1. From within the Azure Machine Learning Studio, navigate to **Compute, Inference Clusters** and select **+ New**.

  ![The Azure Machine Learning Studio Compute, Inference Clusters section is shown with the + New button highlighted.](media/setup-aks-01.png 'Create New Inference Cluster')

1. In the `Select virtual machine` dialog, select a location closest to your AML Workspace, select a VM size **Standard_D3_v2** or equivalent and then select **Next**.

  ![The Select virtual machine dialog is shown with the selected VM location, selected VM size, and the Next button highlighted.](media/setup-aks-02.png 'Select Virtual Machine')

1. In the `Configure Settings` dialog, provide the following values and then select **Create**:

   - **Compute name**: `aks-cluster01`
   - **Cluster purpose**: `Dev-test`
   - **Number of nodes**: `1`
   - **Network configuration**: `Basic`

 ![The Configure Settings dialog is shown populated with the values above, and the Create button highlighted.](media/setup-aks-03.png 'Configure Settings')

### Task 4: Setup Azure DevOps Agent

In order to complete the lab, you need an DevOps agent to run your build and release pipeline jobs. You have two options for the types of agents you can use to run your pipeline jobs:

1. Microsoft-hosted agents
1. Self-hosted agents

**Option 1: Configure Microsoft-hosted agents**

Microsoft has temporarily disabled the free grant of parallel jobs running on Microsoft-hosted agents for public projects and for certain private projects. If you do not already have an approved free grant for parallel jobs, you can request the grant by submitting a request [here](https://aka.ms/azpipelines-parallelism-request). **Please note that it takes about 2-3 business days to respond to your free grant requests**. The other option is to configure and pay for parallel jobs as per instructions [here](https://docs.microsoft.com/en-us/azure/devops/pipelines/licensing/concurrent-jobs?view=azure-devops&tabs=ms-hosted).

**Option 2: Setup and configure self-hosted agents**

For this option, we will look at steps to setup and configure a self-hosted agent that can be used to run your pipeline jobs.

1. Sign in to [Azure DevOps](http://dev.azure.com).

1. Select **User setting, Personal Access Tokens**.

    ![Azure DevOps home page is shown with the user setting menu open and the Personal Access Tokens option selected.](media/setup-pat1.png 'Personal Access Tokens')

1. Select **+ New Token** and provide the following information and then select **Create**:

    - **Name**: `mlops-agent`
    - **Organization**: `Select your organization`
    - **Full access**: `Selected`

    ![Create new personal access token dialog is shown populated with the values above, and the Create button is highlighted.](media/setup-pat2.png 'Create New Personal Access Token')

1. Save the token somewhere safe and accessible for later use during the setup and close the window.

   ![Success dialog is shown, and the Copy and Close buttons are highlighted.](media/setup-pat3.png 'Personal Access Token')

1. From within Azure DevOps, navigate to **Organization Settings, Agent pools** and then select **Add pool**.

   ![Agent pools section under organization settings is shown, and the Add pool button is highlighted.](media/setup-agent-pool1.png 'Add Pool')

1. In the `Add agent pool` dialog provide the following information and then select **Create**:
 
    - **Pool type**: `Self-hosted`
    - **Name**: `MCW Agent Pool`
    - **Grant access permission to all pipelines**: `Selected`
    - **Auto-provision this agent pool in all projects**: `Selected`

    ![Add gent pool token dialog is shown populated with the values above, and the Create button is highlighted.](media/setup-agent-pool2.png 'Add Agent Pool')

1. Navigate to **MCW Agent Pool, Agents** and then select **New agent**.

    ![The Agents section of the MCW Agent Pool page is shown, and the New agent button is highlighted.](media/setup-agent-pool3.png 'Add New Agent')

1. From the `Get the agent` dialog, select **Linux, x64**, copy `Download the agent URL` and save it for later use during the setup, and then close the dialog.

    ![The Linux, x64 section of the Get the agent dialog is shown, and the Copy button is highlighted.](media/setup-agent-pool4.png 'Get the Agent')


1. From within Azure Portal, navigate to ***Virtual machines** and then select **+ Create, + Virtual machine**.

1. In the `Create a virtual machine` dialog, provide the following values and then select **Review + create**:

    - **Subscription**: Select the Azure subscription that you want to use.
    - **Resource group**: Use an existing resource group in your subscription or enter a name to create a new resource group.
    - **Virtual machine name**: **mlops-agent**
    - **Region**: Select the region closest to your users and the data resources.
    - **Image**: **Ubuntu Server 18.04 LTS - Gen 1**
    - **Size**: **Standard_D2**
    - **Authentication type**: **password**
    - **Username**: **mlopsuser**
    - **Password**: Provide a password and save it for later use.
    - **Public inbound ports**: **Allow selected ports**
    - **Select inbound ports**: **SSH (22)**

    ![The Create a virtual machine dialog is shown populated with the values above.](media/setup-vm1.png 'Create Virtual Machine')

1. On the `Review + create` section, select **Create**. It will take few minutes for the VM to be deployed. Continue below once the VM deployed and ready.

1. From the `Overview` section of the virtual machine, copy the **Public IP address** and save it for later use.

   ![Virtual Machine Overview page is shown with copy Public IP address button is highlighted.](media/setup-vm2.png 'Virtual Machine Overview')

1. From a `Azure cloud shell` or `terminal` or `command prompt`, run the following commands:

    - `ssh mlopsuser@xx.xxx.xxx.xxx` (replace the IP address with your VMs public IP address)
       - If you are prompted: `Are you sure you want to continue connecting (yes/no/[fingerprint])?`, type `yes`
    - Provide password for `mlopsuser`

1. Once you are logged into the VM, run the following commands:

   - `curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash`
   - `az extension add --name azure-cli-ml`
    - `curl -O [Download the agent URL copied above]`
        - For example, `curl -O https://vstsagentpackage.azureedge.net/agent/2.191.1/vsts-agent-linux-x64-2.191.1.tar.gz`
   - `mkdir myagent && cd myagent`
   - `tar zxvf ../vsts-agent-linux-x64-2.191.1.tar.gz` (make sure that the tar.gz file name is the same as the one downloaded above)
   - `./config.sh`
       - Accept the Team Explorer Everywhere license agreement now? `Y`
       - Enter server URL > [Provide your Azure DevOps organization URL] (For example, `https://dev.azure.com/organization-name`)
       - Enter authentication type (press enter for PAT) > press enter
       - Enter personal access token > [Provide the PAT saved above]
       - Enter agent pool (press enter for default) > `MCW Agent Pool`
       - Enter agent name (press enter for mlops-agent) > press enter
       - Enter work folder (press enter for _work) > press enter
   - `sudo ./svc.sh install`
   - `sudo ./svc.sh start`
      > **Note**: to stop the agent run: `sudo ./svc.sh stop`. If required, you can find more details on setting up and configuring Self-hosted Linux agents [here](https://docs.microsoft.com/en-us/azure/devops/pipelines/agents/v2-linux?view=azure-devops).

1. From within Azure DevOps, navigate to **Organization Settings, Agent Pools, MCW Agent Pool** and select the **Agents** tab. Confirm that the `mlops-agent` is `online`.

  ![The Agents tab of MCW Agent Pool showing the status of the mlops-agent as online.](media/check-agent-status.png 'MCW Agent Pool Status')

You should follow all steps provided *before* performing the Hands-on lab.
