#TYDZIEN3.4 „Spróbuj na koniec zmodyfikować template tak, by nazwa użytkownika i hasło do każdej maszyny z pkt. 2 było pobierane z KeyVault.„

```
$rg = "trr-kv-rg"
$location = "westeurope"
$keyvaultName = "trr-hr-prod-vmub-kv"
$secretName = "vmSecretAdminPassword"
$value = "passwordP@SSWORD"

az group create --name $rg -l $location
az keyvault create --name $keyvaultName" -g $rg
az keyvault secret set --vault-name $keyvaultName --name $secretName --value $value

```
