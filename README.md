# Qualite_eau_databricks_dlt

A training brief of data ingestion with Databricks and DLTHub.

## Prérequis

Python (développé avec 3.12), un compte Azure

## Configurations
 
Cloner le projet. Créer un dépôt GitHub.  
Créer un token personnel sur GitHub:  
Settings > Developer settings > Personal access tokens (classic)  
Ajouter le token dans les secrets du dépôt GitHub:  
Settings > Secrets > Actions > New repository secret.   
Nom : GH_TOKEN

En cas de changement de nom, changer également dans .github/workflows/release.yml  

Dans Azure, créer un groupe de ressources, un compte de stockage et un conteneur.  
Récupérer la clé d'accès. 

Créer un workspace Databricks.  
Dans le cas où les droits sont insuffisants pour créer un scope (pour les variables d'environnement dans Databricks), créer un token Databrikc et passer par le CLI Databricks ainsi:  

    uv add databricks-cli  
    uv run databricks configure --token 

        Databricks Host (should begin with https://): https://<votre identifiant commençant par adb->.azuredatabricks.net  
        Token: <votre token>  

    uv run databricks secrets create-scope --scope <nom_du_scope>
    uv run databricks secrets put --scope <nom_du_scope> --key storage-account-name --string-value "<nom_du_compte_de_stockage>"
    uv run databricks secrets put --scope nom_du_scope --key storage-account-key --string-value "<cle_d_acces_compte_stockage>"  
Associer le workspace Databricks et le dépôt GitHub:  
Créer>Dossier git>  
renseigner les informations.  

## Travail sur les données

L'ingestion et nettoyage des données peuvent commencer. Créer les notebooks nécessaires et démarrer le cluster pour les exécuter.  



