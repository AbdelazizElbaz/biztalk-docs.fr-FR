---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-jd-edwards-enterpriseone/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: 7dbc9ef8624404b9fa7bdcb7b6a21b2d2a4c69f2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="importing-binding-files"></a>importation des fichiers de liaison
Cette rubrique fournit des informations sur le processus d'importation lors du déploiement de l'adaptateur BizTalk pour JD Edwards EnterpriseOne. Lors du redéploiement d'un fichier de liaison (et de l'assembly) sur un ordinateur cible, les ports d'envoi et les emplacements de réception sont remplacés par ceux qui se trouvent dans le fichier de liaison XML lors de leur réimportation.  
  
### <a name="to-clean-the-target-computer"></a>Pour nettoyer l'ordinateur cible  
  
-   Supprimez les ports d’envoi et emplacements de réception liés à l’orchestration.  
  
     Si Visual Studio n'est pas installé sur l'ordinateur cible, vous pouvez supprimer les ports en exécutant les scripts suivants :  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\  
  
     Remove Send Port\VBScript\RemoveSendPort.vbs  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\  
  
     Remove Receive Port\VBScript\RemoveReceivePort.vbs  
  
     Par exemple, à l'invite de commandes, exécutez :  
  
     **cscript RemoveSendPort.vbs \<nom du port d’envoi\>**  
  
## <a name="see-also"></a>Voir aussi  
 [Importer le JD Edwards EnterpriseOne application](../core/deploying-biztalk-adapter-for-jd-edwards-enterpriseone.md)