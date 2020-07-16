### Task 1: Create a system-assigned managed identity for your Function App to connect to Key Vault

In order for your Function App to be able to access Key Vault to read the secrets, you must [create a system-assigned managed identity](https://docs.microsoft.com/azure/app-service/overview-managed-identity#adding-a-system-assigned-identity) for the Function App, and [create an access policy in Key Vault](https://docs.microsoft.com/azure/key-vault/key-vault-secure-your-key-vault#key-vault-access-policies) for the application identity.

1. Open the **ServerlessArchitecture** resource group, and then select the Azure Function App you created whose name ends with **FunctionApp**. This is the one you created using the **.NET Core** runtime stack. If you did not use this naming convention, that's fine. Just be sure to make note of the name so you can distinguish it from the Function App you will be developing using the portal later on.

    ![In the ServerlessArchitecture resource group, the TollBoothFunctionApp is selected.](media/image33.png 'ServerlessArchitecture resource group')

2. Select **Identity** in the left-hand menu. Within the **System assigned** tab, switch **Status** to **On**. Select **Save**.

    ![In the Identity blade, the System assigned tab is selected with the Status set to On and the Save button is highlighted.](media/function-app-identity.png "Identity")

