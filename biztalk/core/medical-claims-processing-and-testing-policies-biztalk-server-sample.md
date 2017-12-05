---
title: "Soins médicaux des revendications de traitement et de test des stratégies (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, business rules
- business rules, examples
ms.assetid: c0bdf7b7-3e55-4560-a5a8-00c5b661d14d
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70cba6055c51371ddaaf99775bd5e7a60e7f3929
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="medical-claims-processing-and-testing-policies-biztalk-server-sample"></a>Soins médicaux revendications le traitement et le tests de stratégies (exemple BizTalk Server)
L'exemple Stratégies de test et de traitement des demandes de remboursement de soins médicaux illustre la création d'un ensemble de règles qui examinent des faits dérivés d'une table de base de données et du document entrant et qui utilisent les objets .NET pour enregistrer les résultats du traitement des demandes de remboursement.  
  
 Cet exemple montre l'exécution de bout en bout du scénario de traitement des demandes de remboursement à l'aide d'une simple application .NET utilisant le Moteur de règles d'entreprise pour exécuter un ensemble de règles relatives aux demandes de remboursement de soins médicaux sur les demandes de remboursement entrantes afin de déterminer l'ÉTAT de la demande de remboursement et la RAISON de l'état.  
  
> [!NOTE]
>  Cet exemple présente également le suivi de l'exécution du Moteur de règles d'entreprise à l'aide d'un fichier de suivi de débogage.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple applique la séquence suivante de règles aux demandes de remboursement envoyées :  
  
1.  Rejette la demande de remboursement si le montant total demandé dépasse le maximum autorisé par la police.  
  
2.  Rejette la demande de remboursement si le nombre de nuits passées à l'hôpital par le client dépasse le maximum autorisé par la police.  
  
3.  Rejette la demande de remboursement si la date sur la demande de remboursement est dans le futur.  
  
4.  Rejette la demande de remboursement si la police n'est pas valide.  
  
5.  Envoie un message au service commercial avec l'ID de police et le nom du client si la police a expiré.  
  
6.  Dans le cas contraire, approuve la demande de remboursement.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 \<*Exemples de chemin d’accès*\>\Business Rules\Medical les revendications de traitement et de test Policies\  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|Cleanup.bat|Utilisé pour annuler le déploiement des assemblys et les supprimer du Global Assembly Cache (GAC). Supprime les ports d'envoi et de réception. Supprime les répertoires virtuels Microsoft Internet Information Services (IIS) le cas échéant.|  
|Create_PolicyValidity_Table.sql|Script SQL qui ajoute une nouvelle table nommée PolicyValidity à l'exemple de base de données Northwind.|  
|Setup.bat|Utilisé pour créer et initialiser cet exemple.|  
|Dans le dossier \Claims :<br /><br /> AssemblyInfo.cs, Claims.csproj, Claims.sln, Claims.cs|Projet, solution, source et les fichiers associés pour la partie de cet exemple qui enregistre le résultat de réclamations, appelée la **puis** partie d’une règle.|  
|Dans le dossier \FactRetrieverForClaimsProcessing :<br /><br /> AssemblyInfo.cs, FactRetrieverForClaimsProcessing.cs, FactRetrieverForClaimsProcessing.csproj, FactRetrieverForClaimsProcessing.sln|Fichiers de projet, de solution, source et associé pour la partie de cet exemple qui fournit l'extracteur de faits à long terme qui extrait des informations de la table PolicyValidity créée par cet exemple.|  
|Dans le dossier \RulesForMedicalClaims :<br /><br /> App.ico, AssemblyInfo.cs, RulesForMedicalClaims.cs, RulesForMedicalClaims.csproj, RulesForMedicalClaims.sln|Projet, solution, source et les fichiers associés pour la partie de cet exemple qui constitue le principal exécutable pour cet exemple (RulesForMedicalClaims.exe) et qui par programme définit et stocke l’ensemble de règles, construit les exemples de faits et exécute ensuite le règle définie à l’aide un **PolicyTester** objet.|  
|Dans le dossier \RulesForMedicalClaims :<br /><br /> MedicalClaims.xsd|Fichier de schéma qui définit la structure des exemples de demandes de remboursement de soins médicaux envoyés à cet exemple.|  
|Dans le dossier \RulesForMedicalClaims :<br /><br /> sampleClaim.xml|Exemple de fichier d'entrée correspondant au schéma défini dans le fichier MedicalClaims.xsd.|  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
  
#### <a name="to-build-and-initialize-the-medical-claims-processing-and-testing-policies-sample"></a>Pour créer et initialiser l'exemple Stratégies de test et de traitement des demandes de remboursement de soins médicaux  
  
1.  Vérifiez que vous disposez de la base de données Northwind sur votre ordinateur.  
  
    > [!IMPORTANT]
    >  Pour exécuter cet exemple, vous devez disposer de la base de données Northwind SQL Server. [Télécharger](https://www.microsoft.com/download/details.aspx?id=23654)et l’installer. 
  
2.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*\>\Business Rules\Medical les revendications de traitement et de test Policies\  
  
3.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   Compilation et déploiement des projets [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour cet exemple, y compris Claims.dll, FactRetrieverForClaimsProcessing.dll et RulesForMedicalClaims.dll.  
  
    > [!NOTE]
    >  Vous devez confirmer que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas signalé d'erreur pendant le processus de création et d'initialisation, avant d'essayer de faire fonctionner cet exemple.  
  
    > [!NOTE]
    >  Si vous choisissez Ouvrir et générer les projets dans cet exemple sans exécuter le fichier Setup.bat, vous devez tout d’abord créer une paire de clés de nom fort à l’aide du Kit de développement .NET Framework Strong Name utility (sn.exe). Celle-ci permet de signer les assemblys obtenus.  
  
    -   Exécution du script SQL fourni, Create_PolicyValidity_Table.sql, à l'aide de l'Analyseur de requêtes SQL. Le script crée la table PolicyValidity avec deux exemples de lignes dans l'exemple de base de données Northwind. Cette table contient deux colonnes : ID et PolicyStatus.  
  
    -   Crée et lie les ports d'envoi et de réception de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
    -   Active l'emplacement de réception, et démarre le port d'envoi.  
  
    -   Inscrit et démarre l’orchestration.  
  
    > [!NOTE]
    >  Pour annuler les modifications effectuées par Setup.bat, exécutez Cleanup.bat. Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
  
#### <a name="to-run-the-medical-claims-processing-and-testing-policies-sample"></a>Pour exécuter l'exemple Stratégies de test et de traitement des demandes de remboursement de soins médicaux  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*\>\Business Rules\Medical les revendications de traitement et de test Policies\RulesForMedicalClaims\bin\Debug\  
  
2.  Exécutez le fichier RulesForMedicalClaims.exe sur la ligne de commande.  
  
    > [!NOTE]
    >  Vous pouvez modifier les valeurs des éléments individuels dans l'exemple de fichier de demande de remboursement sampleClaim.xml, puis exécuter l'exemple de façon répétée. Les résultats attendus des différentes valeurs de ces éléments sont affichés dans la liste suivante.  
  
 Les scénarios de sortie en fonction des différentes combinaisons de valeurs dans l'exemple de fichier de demande de remboursement envoyé sont les suivants :  
  
-   Pour une demande de remboursement dont le montant dépasse 1000 $, le résultat suivant est obtenu :  
  
    ```  
    Status:  REJECTED!  
    Reason:  Amount of claim has exceeded Policy limit  
    ```  
  
-   Pour une demande de remboursement dont le nombre de nuits dépasse 10, le résultat suivant est obtenu :  
  
    ```  
    Status:  REJECTED!  
    Reason:  Amount of Nights has exceeded Policy limit  
    ```  
  
-   Pour une demande de remboursement dont la date n'est pas valide (date > date actuelle), le résultat suivant est obtenu :  
  
    ```  
    Status:  REJECTED!  
    Reason:  Cannot submit claims for future dates!  
    ```  
  
-   Pour une revendication avec un ID de stratégie n’est pas valide (par exemple, en modifiant le **ID** ont une valeur de 2) en raison de l’expiration de la stratégie, le résultat suivant est obtenu :  
  
    ```  
    Sending to Renewal Department for Customer Smir with Policy # 2  
    Status:  REJECTED!  
    Reason:  Policy ID is invalid  
    ```  
  
-   Pour une demande de remboursement valide, le résultat suivant est obtenu :  
  
    ```  
    Status:  Claim Accepted!  
    Reason:  
    ```  
  
    > [!NOTE]
    >  Un fichier texte, outputtrace.txt, est créé dans le dossier ...\RulesForMedicalClaims\bin\Debug à chaque exécution de cet exemple. Il contient un suivi de débogage de l'exécution des règles, et il est créé après chaque cycle d'exécution dans le dossier \RulesForMedicalClaims\bin\Debug. Vous pouvez examiner ce fichier pour afficher le suivi de sortie de l'exécution des règles.  
  
## <a name="comments"></a>Commentaires  
 Les sources de faits utilisées dans l'évaluation de l'ensemble de règles sont les suivantes :  
  
-   Un extracteur de faits à long terme, un. Application basée sur le réseau qui implémente le **IFactReriever** de l’interface, est créé dans le dossier FactRetrieverForClaimsProcessing. Il est utilisé par la stratégie de traitement des demandes de remboursement de soins médicaux pour extraire des données (sous forme de groupes de données) de la base de données PolicyValidity ainsi que pour l'évaluation de condition de règles.  
  
-   La demande de remboursement est un document XML contenant les informations suivantes, stockées dans des éléments frères : Nom, ID, Montant, Nuits et Date.  
  
-   UN FICHIER. Bibliothèque de classes NET (Claims), avec un **ClaimResults** classe est utilisée pour enregistrer l’état et la raison de la demande à l’aide des propriétés et pour envoyer un message (si la stratégie n’est pas valide) en appelant le **SendLeads** méthode avec l’ID et le nom en tant que paramètres.  
  
 En fonction de ces sources de faits, vous pouvez décrire de manière informelle les règles définies pour ce scénario comme suit :  
  
1.  Vérifiez si la demande de remboursement entrante est valide. La demande de remboursement n'est pas valide si le montant dépasse la limite autorisée pour une demande de remboursement, si la police a expiré (vérification de la table de base de données), si le nombre de nuits dépasse la limite autorisée et si la demande de remboursement est effectuée dans le futur. Si la demande de remboursement a été déterminée comme non valide, définissez l'ÉTAT et la RAISON de la demande de remboursement de manière appropriée.  
  
2.  Si l'ID de police de la demande de remboursement entrante a expiré, envoyez un message (avec l'ID de police et le nom du client) au service de renouvellement des polices.  
  
3.  Si la demande de remboursement est valide, définissez l'ÉTAT et la RAISON de la demande de remboursement de manière appropriée.  
  
 Une représentation plus formelle des règles et de leurs liaisons à terme est la suivante :  
  
-   **Règle 1. Vérification de la quantité**  
  
    ```  
    IF Amount in the XML document is > 1000  
      AND  
    IF Claims.ClaimResults object has not been modified (if ClaimResults.RESULT = null)  
  
    THEN Claims.ClaimResults.Status = "REJECTED"\  
         &&  
         Claims.ClaimResults.Reason = "Amount of claim has exceeded limit"  
         &&  
         Assert this object back into working memory  
  
    ```  
  
-   **Règle 2. Nuits passées à l’hôpital**  
  
    ```  
    IF number of nights in the XML document is > 10  
      AND  
    IF Claims.ClaimResults object has not been modified (if ClaimResults.RESULT = null)  
  
    THEN Claims.ClaimResults.Status = "REJECTED"  
         &&  
         Claims.ClaimResults.Reason = "Amount of claim has exceeded limit"  
         &&  
         Assert this object back into working memory  
  
    ```  
  
-   **Règle 3. Validité de date**  
  
    ```  
    IF date on the incoming XML claim is > Today  
      AND   
    IF Claims.ClaimResults object has not been modified (if ClaimResults.RESULT = null)  
  
    THEN Claims.ClaimResults.Status = "REJECTED"  
         &&  
         Claims.ClaimResults.Reason = "Cannot submit claims in the future!"  
         &&  
         Assert this object back into working memory  
  
    ```  
  
-   **Règle 4. Validité de la stratégie**  
  
    ```  
    IF Policy is invalid for the ID in the XML claim (check database)  
      AND  
    IF Claims.ClaimResults object has not been modified (if ClaimResults.RESULT = null)  
  
    THEN Claims.ClaimResults.Status = "REJECTED"  
         &&  
         Claims.ClaimResults.Reason = "Policy Invalid"  
         &&  
         Assert this object back into working memory  
  
    ```  
  
-   **Règle 5. Prospects**  
  
    ```  
    IF Claim.ClaimResults.Reason = "Policy invalid"  
  
    THEN send a lead to the policy department by invoking the function Claim.ClaimResults.SendLead with customer ID and Name from the incoming XML document.  
  
    ```  
  
-   **Règle 6. Demande de remboursement acceptée**  
  
    ```  
    IF Claim.ClaimResults.Status = null  
  
    THEN Set the claim status to be valid  
         &&  
         Send the lead to the sales department  
  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Règles d’entreprise (dossier d’exemples BizTalk Server)](../core/business-rules-biztalk-server-samples-folder.md)