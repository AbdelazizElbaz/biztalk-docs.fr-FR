---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-peoplesoft-enterprise/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: 907c21377a6affd5a99576137a5babaa1626c135
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="import-binding-files"></a>Importer des fichiers de liaison

## <a name="overview"></a>Vue d'ensemble
Avant d'importer un fichier de liaison à l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vérifiez les éléments suivants :  
  
-   CLASSPATH pointe vers un emplacement particulier pour les fichiers spécifiques à PeopleSoft. Vérifiez que l’emplacement de ces fichiers est le même sur le nouvel ordinateur, ou modifier le fichier de liaison.  
  
-   Les dossiers pour les réponses doivent exister et être identiques sur le nouvel ordinateur, ou modifier le fichier de liaison.  
  
-   S'ils sont présents dans la configuration, les mots de passe du système PeopleSoft Enterprise sont enregistrés dans le fichier de liaison sous la forme *****. 
  
> [!NOTE]
>  Le déploiement remplace la configuration de l'emplacement de réception. Lorsque vous déployez un fichier de liaison et l’assembly sur un ordinateur cible, les ports d’envoi et emplacements de réception sont remplacés par ceux dans le fichier de liaison XML lorsqu’ils sont importés.  
  
 Pour obtenir des instructions détaillées sur l'importation des fichiers de liaison, consultez la rubrique « Importation des liaisons dans un groupe BizTalk » dans la documentation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="clean-the-target-computer"></a>Nettoyer l’ordinateur cible  
Pour nettoyer l’ordinateur cible pour le déploiement de la nouvelle application, supprimez les ports d’envoi et emplacements de réception liés à l’orchestration.  
  
Si Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] n'est pas installé sur l'ordinateur cible, vous pouvez supprimer les ports en exécutant les scripts suivants :  
  
**\<Microsoft BizTalk Server\>\SDK\Samples\Admin\WMI\Remove envoyer Port\VBScript\RemoveSendPort.vbs**  
  
**\<Microsoft BizTalk Server\>\SDK\Samples\Admin\WMI\Remove Port\VBScript\RemoveReceivePort.vbs de réception**  
  
Par exemple, à une invite de commandes, exécutez :  
  
**cscript RemoveSendPort.vbs \<nom du port d’envoi\>**  
  
