---
title: "Définir la propriété du Gestionnaire d’envoi (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SMTP adapters, examples
- examples, SMTP adapters
- send handlers, properties
ms.assetid: eb6ae2f2-528f-44ec-bca4-f37006893ff2
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0e14f58cbdd07a8c13dec6cd44fbc95584f2ecc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="set-send-handler-property-biztalk-server-sample"></a>Définir la propriété du Gestionnaire d’envoi (exemple BizTalk Server)
L'exemple de définition des propriétés du gestionnaire d'envoi (Set Send Handler Property) illustre la définition des informations de configuration XML pour un gestionnaire d'envoi SMTP (Simple Mail Transfer Protocol).  
  
> [!WARNING]
>  Les scripts de déploiement devenus inutiles après le déploiement doivent être supprimés. Les scripts d'administration et autres scripts conservés doivent être sécurisés à l'aide de listes de contrôle d'accès et étroitement surveillés.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Le script Visual Basic Scripting Edition (VBScript) dans le fichier de script de cet exemple décrit l'exécution des opérations suivantes à l'aide du fournisseur WMI BizTalk Server :  
  
-   pour un nom du gestionnaire d'envoi, création d'une requête pour obtenir la liste des gestionnaires d'envoi correspondants.  
  
-   définition des informations de configuration XML pour un gestionnaire d'envoi SMTP.  
  
-   gestion de toutes erreurs de telle sorte que les informations significatives soient renvoyées à l'utilisateur.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 Les fichiers de l'exemple se trouvent dans l'emplacement SDK suivant :  
  
 \<*Exemples de chemin d’accès*> \Admin\WMI\Set Property\ du Gestionnaire d’envoi  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|Dans le dossier \VBScript :<br /><br /> ConfigureSMTP.vbs|Fichier VBScript qui utilise des paramètres spécifiant un gestionnaire d'envoi SMTP et une adresse de messagerie d'expéditeur.|  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
 L'exemple Set Send Handler Property est constitué d'un seul fichier VBScript que vous ne devez ni créer ni initialiser.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
  
#### <a name="to-run-the-set-send-handler-property-sample"></a>Pour exécuter l'exemple Set Send Handler Property  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*> \Admin\WMI\Set Property\VBScript\ du Gestionnaire d’envoi  
  
2.  Exécutez le fichier ConfigureSMTP.vbs à l'aide du programme cscript en transmettant l'argument de ligne de commande suivant :  
  
    -   **\<**   
         ***SMTPServerName* >.** Nom du serveur SMTP à utiliser pour envoyer le message.  
  
    -   **\<**   
         ***FromEmailAddress* >.** Adresse de messagerie qui sera utilisée comme adresse d'expéditeur.  
  
         Exemple :  
  
        ```  
        cscript ConfigureSMTP.vbs MyBusinessSMTPServer someone@example.com  
        ```  
  
## <a name="comments"></a>Commentaires  
 Toutes les tâches effectuées dans la console Administration de BizTalk Server peuvent également être effectuées à l'aide d'un script qui accède au modèle objet WMI de Windows.  
  
 Le fichier de script ConfigureSMTP.vbs contient des commentaires détaillés avec davantage d'explications sur les opérations qu'il effectue. Pour plus d’informations, consultez Windows Management Instrumentation à [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).  
  
## <a name="see-also"></a>Voir aussi  
 [Admin-WMI (dossier d’exemples BizTalk Server)](../core/admin-wmi-biztalk-server-samples-folder.md)