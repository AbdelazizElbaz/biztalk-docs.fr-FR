---
title: Remove Send Port (exemple BizTalk Server) | Documents Microsoft
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
- send ports, deleting
- deleting, send ports
ms.assetid: e6643525-fa9f-4d39-880f-314749a68471
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e8b82af2be42342d51429e42d1952816ee0dd07a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="remove-send-port-biztalk-server-sample"></a>Remove Send Port (exemple BizTalk Server)
L'exemple de suppression d'un port d'envoi (Remove Send Port) illustre la désinscription et la suppression d'un ou plusieurs ports d'envoi.  
  
> [!WARNING]
>  Les scripts de déploiement devenus inutiles après le déploiement doivent être supprimés. Les scripts d'administration et autres scripts conservés doivent être sécurisés à l'aide de listes de contrôle d'accès et étroitement surveillés.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Le script Visual Basic Scripting Edition (VBScript) dans le fichier de script de cet exemple décrit l'exécution des opérations suivantes à l'aide du fournisseur WMI BizTalk Server :  
  
-   pour un nom de port d'envoi, création d'une requête pour obtenir la liste des ports d'envoi correspondants.  
  
    > [!NOTE]
    >  En général, un seul port d'envoi correspond à un nom donné.  
  
-   désinscription de ces ports d'envoi.  
  
-   suppression de ces ports d'envoi.  
  
-   gestion de toutes erreurs de telle sorte que les informations significatives soient renvoyées à l'utilisateur.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 L'exemple se trouve dans l'emplacement SDK suivant :  
  
 \<*Exemples de chemin d’accès*\>\Admin\WMI\Remove LPT1\ d’envoi  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|Dans le dossier \VBScript :<br /><br /> RemoveSendPort.vbs|Fichier VBScript qui récupère un paramètre spécifiant un ou plusieurs ports d'envoi à désinscrire et supprimer.|  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
 L'exemple Remove Send Port est constitué d'un seul fichier VBScript que vous ne devez ni créer ni initialiser.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
  
#### <a name="to-run-the-remove-send-port-sample"></a>Pour exécuter l'exemple Remove Send Port  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*\>\Admin\WMI\Remove Port\VBScript\ de réception  
  
2.  Exécutez le fichier RemoveSendPort.vbs à l'aide du programme cscript en transmettant l'argument de ligne de commande suivant :  
  
     **\<** ***SendPortName* \>.** Nom du ou des ports d'envoi à supprimer. Si le nom du port d'envoi contient des espaces, placez-le entre guillemets.  
  
     Exemple :  
  
    ```  
    cscript RemoveSendPort.vbs "My Business Send Port"  
    ```  
  
## <a name="comments"></a>Commentaires  
 Toutes les tâches effectuées dans la console Administration de BizTalk Server peuvent également être effectuées à l'aide d'un script qui accède au modèle objet WMI de Windows.  
  
 Le fichier de script RemoveSendPort.vbs contient des commentaires détaillés avec davantage d'explications sur les opérations qu'il effectue. Pour plus d’informations, consultez Windows Management Instrumentation à [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).  
  
## <a name="see-also"></a>Voir aussi  
 [Admin-WMI (dossier d’exemples BizTalk Server)](../core/admin-wmi-biztalk-server-samples-folder.md)