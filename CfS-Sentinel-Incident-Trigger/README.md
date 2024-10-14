# Copilot for Security - Sentinel Incident trigger
Author: Sergio Medina Vallejo

Use the following button to start the deployment of an Azure Logic App playbook integrated with Copilot for Security. It will utilize a Microsoft Sentinel incident as trigger to extract the Incident ID and invoke a Copilot for Security promptbook to perform enrichment. The results of the final prompt will be sent back to the Incident as a Comment.<br>
Use this button to ![Deploy to Azure](https://aka.ms/deploytoazurebutton)

Considerations: <br>
1. The Run Copilot for Security Promptbook step has a timeout of 50 minutes. This will avoid any infinite execution when for example the SCUs are exhausted.
2. The key part for extracting the content of the comment in the last step is:
        last(body('Run_a_Copilot_for_Security_promptbook')['evaluationResultList'])['evaluationResultContent']
3. Execute the playbook using a user account. It will allow debugging the sessions. Running it with a service principal will not allow access to the session.
