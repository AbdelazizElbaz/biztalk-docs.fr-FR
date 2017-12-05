---
title: "(Exemple BizTalk Server) de Port de réception de supprimer | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive ports, examples
- deleting, receive ports
- examples, receive ports
- receive ports, deleting
ms.assetid: de97d914-b8e8-4365-8041-3b455c351f86
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2d15442da8afd4829245b742bdd45af8f7d1f832
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="remove-receive-port-biztalk-server-sample"></a>Suppression de réception Port (exemple BizTalk Server)
L'exemple de suppression d'un port de réception (Remove Receive Port) illustre la suppression d'un ou plusieurs ports de réception.  
  
> [!WARNING]
>  Les scripts de déploiement devenus inutiles après le déploiement doivent être supprimés. Les scripts d'administration et autres scripts conservés doivent être sécurisés à l'aide de listes de contrôle d'accès et étroitement surveillés.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Le script Visual Basic Scripting Edition (VBScript) dans le fichier de script de cet exemple décrit l'exécution des opérations suivantes à l'aide du fournisseur WMI BizTalk Server :  
  
-   pour un nom de port de réception, création d'une requête pour obtenir la liste des ports de réception correspondants ;  
  
    > [!NOTE]
    >  En général, un seul port de réception correspond à un nom donné.  
  
-   suppression de ces ports de réception ;  
  
-   gestion de toutes erreurs de telle sorte que les informations significatives soient renvoyées à l'utilisateur.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 Les exemples se trouvent dans l'emplacement SDK suivant :  
  
 \<*Exemples de chemin d’accès*\>\Admin\WMI\Remove LPT1\ de réception  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|Dans le dossier \VBScript :<br /><br /> RemoveReceivePort.vbs|Fichier VBScript qui récupère un paramètre spécifiant un ou plusieurs ports de réception à supprimer.|  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
 L'exemple Remove Receive Port est constitué d'un seul fichier VBScript que vous ne devez ni créer ni initialiser.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
  
#### <a name="to-run-this-sample"></a>Pour exécuter l'exemple  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*\>\Admin\WMI\Remove Port\VBScript\ de réception  
  
2.  Exécutez le fichier RemoveReceivePort.vbs à l'aide du programme cscript en transmettant l'argument de ligne de commande suivant :  
  
     **\<** ***ReceivePortName* \>** . Nom du ou des ports de réception à supprimer. Si le nom du port de réception contient des espaces, placez-le entre guillemets.  
  
     Exemple :  
  
    ```  
    cscript RemoveReceivePort.vbs "My Business Receive Port"  
    ```  
  
## <a name="comments"></a>Commentaires  
 Toutes les tâches effectuées dans la console Administration de BizTalk Server peuvent également être effectuées à l'aide d'un script qui accède au modèle objet WMI de Windows.  
  
 Le fichier de script RemoveReceivePort.vbs contient des commentaires détaillés avec davantage d'explications sur les opérations qu'il effectue. Pour plus d’informations, consultez Windows Management Instrumentation à [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).  
  
## <a name="see-also"></a>Voir aussi  
 [Admin-WMI (dossier d’exemples BizTalk Server)](../core/admin-wmi-biztalk-server-samples-folder.md)