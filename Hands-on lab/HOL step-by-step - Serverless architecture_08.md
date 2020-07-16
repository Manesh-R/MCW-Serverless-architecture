### Task 7: Retrieve the URI for each secret

When you set the App Settings for the Function App in the next section below, you will need to reference the URI of a secret in Key Vault, including the version number. To do this, perform the following steps for each secret and **copy the values** to Notepad or similar text application.

1. Open your Key Vault instance in the portal.

2. Select **Secrets** under Settings in the left-hand menu.

3. Select the secret whose URI value you wish to obtain.

4. Select the **Current Version** of the secret.

    ![The secret's current version is selected.](media/key-vault-secret-current-version.png "Current Version")

5. Copy the **Secret Identifier**.

    ![The Secret Identifier field is highlighted. Next to this field is a copy button.](media/key-vault-secret-identifier.png "Secret Identifier")

    When you add the Key Vault reference to this secret within a Function App's App Settings, you will use the following format: `@Microsoft.KeyVault(SecretUri={referenceString})`, where `{referenceString}` is replaced by the Secret Identifier (URI) value above. **Be sure to remove the curly braces (`{}`)**.

    For example, a complete reference would look like the following:

    `@Microsoft.KeyVault(SecretUri=https://tollboothvault.vault.azure.net/secrets/blobStorageConnection/d6ea0e39236348539dc33565e031afc3)`

When you are done creating the values, you should have a list similar to the following:

```text
@Microsoft.KeyVault(SecretUri=https://tollboothvault.vault.azure.net/secrets/blobStorageConnection/771aa40adac64af0b2aefbd741bd46ef)
@Microsoft.KeyVault(SecretUri=https://tollboothvault.vault.azure.net/secrets/computerVisionApiKey/ce228a43f40140dd8a9ffb9a25d042ee)
@Microsoft.KeyVault(SecretUri=https://tollboothvault.vault.azure.net/secrets/cosmosDBAuthorizationKey/1f9a0d16ad22409b85970b3c794a218c)
@Microsoft.KeyVault(SecretUri=https://tollboothvault.vault.azure.net/secrets/eventGridTopicKey/e310bcd71a72489f89b6112234fed815)
```

## Exercise 2: Develop and publish the photo processing and data export functions

**Duration**: 45 minutes

Use Visual Studio and its integrated Azure Functions tooling to develop and debug the functions locally, and then publish them to Azure. The starter project solution, TollBooths, contains most of the code needed. You will add in the missing code before deploying to Azure.

