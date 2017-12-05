---
title: "Activer la réception emplacement (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, examples
- receive locations, enabling
- examples, receive locations
ms.assetid: dd04b38a-634d-4c9a-b31a-2f226fa91d19
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fd2df85f051285e999660dc3765855d22c708939
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="enable-receive-location-biztalk-server-sample"></a>Activer la réception emplacement (exemple BizTalk Server)
L'exemple d'activation d'un emplacement de réception (Enable Receive Location) décrit l'activation d'un emplacement de réception, et éventuellement, la définition de l'URL de transport entrant pour cet emplacement de réception.  
  
> [!WARNING]
>  Les scripts de déploiement devenus inutiles après le déploiement doivent être supprimés. Les scripts d'administration et autres scripts conservés doivent être sécurisés à l'aide de listes de contrôle d'accès et étroitement surveillés.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Le script Microsoft Visual Basic Scripting Edition (VBScript) dans le fichier de script de cet exemple décrit l'exécution des opérations suivantes à l'aide du fournisseur WMI BizTalk Server :  
  
-   pour un nom de port de réception et un emplacement de réception, création d'une requête pour obtenir la liste des emplacements de réception correspondants ;  
  
-   définition de l'URL de transport entrant pour un emplacement de réception (relative au chemin d'installation) ;  
  
-   activation d'un emplacement de réception ;  
  
-   gestion de toutes erreurs de telle sorte que les informations significatives soient renvoyées à l'utilisateur.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 L'exemple se trouve dans l'emplacement SDK suivant :  
  
 \<*Exemples de chemin d’accès*\>\Admin\WMI\Enable Location\ de réception  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|Dans le dossier \VBScript :<br /><br /> EnableRecLoc.vbs|Fichier VBScript qui utilise des paramètres spécifiant un emplacement de réception à activer, et éventuellement, une nouvelle valeur pour l'URL de transport entrant associée à cet emplacement de réception.|  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
 L'exemple d'activation d'un emplacement de réception est constitué d'un seul fichier VBScript que vous ne devez ni créer ni initialiser.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
  
#### <a name="to-run-this-sample"></a>Pour exécuter l'exemple  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*\>\Admin\WMI\Enable Location\VBScript\ de réception  
  
2.  Exécutez le fichier EnableRecLoc.vbs à l'aide du programme cscript en transmettant les arguments de ligne de commande suivants (le troisième argument est facultatif) :  
  
    -   **\<** ***ReceivePortName* \>.** Nom du port de réception contenant l'emplacement de réception à activer. Si le nom du port de réception contient des espaces, placez-le entre guillemets.  
  
    -   **\<** ***ReceiveLocationName* \>.** Nom de l'emplacement de réception à activer au sein du port de réception spécifié. Si le nom de l'emplacement de réception contient des espaces, placez-le entre guillemets.  
  
    -   **\<** ***InboundTransportURI* \>.** URI d'adaptateur de réception, relative à l'emplacement d'installation du produit, que vous pouvez modifier en spécifiant cet argument. Si l'URI de l'adaptateur entrant contient des espaces, placez-le entre guillemets.  
  
         Exemple :  
  
        ```  
        cscript EnableRecLoc.vbs "My Business Receive Port" MyBusinessReceiveLocation  
        ```  
  
         -OU-  
  
        ```  
        cscript EnableRecLoc.vbs MyBusinessReceivePort "My Business Receive Location" SDK\Samples\HelloWorld\In\*.xml  
        ```  
  
## <a name="comments"></a>Commentaires  
 Toutes les tâches effectuées dans la console Administration de BizTalk Server peuvent également être effectuées à l'aide d'un script qui accède au modèle objet WMI de Windows.  
  
 Le fichier de script EnableRecLoc.vbs contient des commentaires détaillés avec davantage d'explications sur les opérations qu'il effectue.  
  
 Pour plus d’informations, consultez Windows Management Instrumentation à [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).  
  
## <a name="see-also"></a>Voir aussi  
 [Admin-WMI (dossier d’exemples BizTalk Server)](../core/admin-wmi-biztalk-server-samples-folder.md)