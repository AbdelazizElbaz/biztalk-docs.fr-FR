---
title: "Port d’envoi de début (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send ports, examples
- examples, send ports
- send ports, starting
ms.assetid: 84e54c9e-e9e8-4bb2-a191-20c29e127dae
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f293d00848c32f6b519349543c8a39824d9bca8c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="start-send-port-biztalk-server-sample"></a>Port d’envoi de début (exemple BizTalk Server)
L'exemple de démarrage d'un port d'envoi (Start Send Port) décrit le démarrage d'un port d'envoi et la définition éventuelle de l'adresse de transport principal lorsque l'adaptateur FILE est utilisé.  
  
> [!WARNING]
>  Les scripts de déploiement devenus inutiles après le déploiement doivent être supprimés. Les scripts d'administration et autres scripts conservés doivent être sécurisés à l'aide de listes de contrôle d'accès et étroitement surveillés.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Le script Visual Basic Scripting Edition (VBScript) dans le fichier de script de cet exemple décrit l'exécution des opérations suivantes à l'aide du fournisseur WMI BizTalk Server :  
  
-   pour un nom de port d'envoi, création d'une requête pour obtenir la liste des ports d'envoi correspondants.  
  
    > [!NOTE]
    >  En général, un seul port d'envoi correspond à un nom donné.  
  
-   définition de l'adresse de transport principal pour ces ports d'envoi (relative au chemin d'installation).  
  
-   démarrage de ces ports d'envoi.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 Les fichiers de l'exemple se trouvent dans l'emplacement SDK suivant :  
  
 \<*Exemples de chemin d’accès*\>\Admin\WMI\Start LPT1\ d’envoi  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|Dans le dossier \VBScript :<br /><br /> StartSendPort.vbs|Fichier VBScript qui utilise des paramètres spécifiant un port d'envoi à démarrer, et éventuellement, une nouvelle valeur pour l'adresse de transport principal associée à ce port.|  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
 L'exemple Start Send Port est constitué d'un seul fichier VBScript que vous ne devez ni créer ni initialiser.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
  
#### <a name="to-run-this-sample"></a>Pour exécuter l'exemple  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*\>\Admin\WMI\Start Port\VBScript\ d’envoi  
  
2.  Exécutez le fichier StartSendPort.vbs à l'aide du programme cscript en transmettant les arguments de ligne de commande suivants (le second argument est facultatif) :  
  
    -   **\<** ***SendPortName* \>.** Nom du port d'envoi à démarrer. Si le nom du port d'envoi contient des espaces, placez-le entre guillemets.  
  
    -   **\<** ***PrimaryTransportAddress* \>.** Adresse de transport principal, relative à l'emplacement d'installation du produit, que vous pouvez modifier en spécifiant cet argument. Si l'adresse de l'adaptateur principal contient des espaces, placez-la entre guillemets.  
  
         Exemple :  
  
        ```  
        cscript StartSendPort.vbs "My Business Send Port" SDK\Samples\HelloWorld\Out\%MessageID%.xml  
        ```  
  
## <a name="comments"></a>Commentaires  
 Toutes les tâches effectuées dans la console Administration de BizTalk Server peuvent également être effectuées à l'aide d'un script qui accède au modèle objet WMI de Windows.  
  
 Le fichier de script StartSendPort.vbs contient des commentaires détaillés avec davantage d'explications sur les opérations qu'il effectue. Pour plus d’informations, consultez Windows Management Instrumentation à [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).  
  
## <a name="see-also"></a>Voir aussi  
 [Admin-WMI (dossier d’exemples BizTalk Server)](../core/admin-wmi-biztalk-server-samples-folder.md)