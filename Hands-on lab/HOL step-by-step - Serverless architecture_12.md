### Task 3: Add Function App to Key Vault access policy

Perform these steps to create an access policy that enables the "Get" secret permission:

1. Open your Key Vault service.

2. Select **Access policies**.

3. Select **+ Add Access Policy**.

    ![In the Key vault Access Policies blade, The Add Access Policy link is highlighted.](media/key-vault-add-access-policy.png "Access policies")

4. Select the **Select principal** section on the Add access policy form.

    ![In the Add access policy form, the Select principal field is highlighted.](media/key-vault-add-access-policy-select-principal.png "Add access policy")

5. In the Principal blade, search for your TollBoothFunctionApp Function App's service principal, select it, then select the **Select** button.

    ![In the Select a principal form, TollBooth is entered into the search field and the Function App's principal is selected in the search results. The Select button is also highlighted.](media/key-vault-principal.png "Principal")

6. Expand the **Secret permissions** and check **Get** under Secret Management Operations.

    ![In the Add access policy form, the Secret Permissions dropdown is expanded with the Get checkbox checked.](media/key-vault-get-secret-policy.png "Add access policy")

7. Select **Add** to add the new access policy.

8. When you are done, you should have an access policy for the Function App's managed identity. Select **Save** to finish the process.

    ![In the list of Key Vault access policies, the policy that was just created is highlighted. The Save button is selected to commit the changes.](media/key-vault-access-policies.png "Access policies")

