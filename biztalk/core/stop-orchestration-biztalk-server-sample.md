---
title: "Arrêter l’Orchestration (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- examples, orchestrations
- orchestrations, stopping
ms.assetid: 83be44e9-819d-4ac5-8b75-84c23e6b5ba2
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b0c88bdeb85b8ad493b85d2569061c35bd516e1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="stop-orchestration-biztalk-server-sample"></a>Arrêter l’Orchestration (exemple BizTalk Server)
L'exemple d'arrêt d'une orchestration (Stop Orchestration) décrit l'arrêt d'une orchestration BizTalk Server et sa désinscription éventuelle.  
  
> [!WARNING]
>  Les scripts de déploiement devenus inutiles après le déploiement doivent être supprimés. Les scripts d'administration et autres scripts conservés doivent être sécurisés à l'aide de listes de contrôle d'accès et étroitement surveillés.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Le script Visual Basic Scripting Edition (VBScript) dans le fichier de script de cet exemple décrit l'exécution des opérations suivantes à l'aide du fournisseur WMI BizTalk Server :  
  
-   pour un nom d'orchestration et un nom d'assembly, création d'une requête pour une orchestration BizTalk Server déployée spécifique ;  
  
-   arrêt de cette orchestration.  
  
-   désinscription de cette orchestration (facultatif).  
  
-   gestion de toutes erreurs de telle sorte que les informations significatives soient renvoyées à l'utilisateur.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 Les fichiers de l'exemple se trouvent dans l'emplacement SDK suivant :  
  
 \<*Exemples de chemin d’accès*\>\Admin\WMI\Stop Orchestration\  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|Dans le dossier \VBScript :<br /><br /> StopOrch.vbs|Fichier VBScript qui utilise des paramètres pour spécifier une orchestration à arrêter et, éventuellement, à désinscrire.|  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
 L'exemple Stop Orchestration est constitué d'un seul fichier VBScript que vous ne devez ni créer ni initialiser.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
  
#### <a name="to-run-this-sample"></a>Pour exécuter l'exemple  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*\>\Admin\WMI\Stop Orchestration\VBScript\  
  
2.  Exécutez le fichier StopOrch.vbs à l'aide du programme cscript en transmettant les arguments de ligne de commande suivants (le troisième argument est facultatif) :  
  
    -   **\<** ***OrchestrationName* \>.** Nom de l'orchestration BizTalk Server à arrêter et, éventuellement, à désinscrire.  
  
    -   **\<** ***AssemblyName* \>.** Nom de l'assembly BizTalk dans lequel l'orchestration spécifiée a été déployée. Si le nom de l'assembly contient des espaces, placez-le entre guillemets.  
  
    -   **Annuler l’inscription.** Chaîne littérale facultative qui permet d'indiquer que l'orchestration spécifiée doit être arrêtée et désinscrite.  
  
         Exemple :  
  
        ```  
        cscript StopOrch.vbs MyBusinessOrchestration "My Business Assembly"  
        ```  
  
         -OU-  
  
        ```  
        cscript StopOrch.vbs MyBusinessOrchestration MyBusinessAssembly Unenlist  
        ```  
  
## <a name="comments"></a>Commentaires  
 Toutes les tâches effectuées dans la console Administration de BizTalk Server peuvent également être effectuées à l'aide de scripts qui accèdent au modèle objet WMI de Windows.  
  
 Le fichier de script StopOrch.vbs contient des commentaires détaillés avec davantage d'explications sur les opérations qu'il effectue. Pour plus d’informations, consultez Windows Management Instrumentation à [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).  
  
## <a name="see-also"></a>Voir aussi  
 [Admin-WMI (dossier d’exemples BizTalk Server)](../core/admin-wmi-biztalk-server-samples-folder.md)