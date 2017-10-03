---
title: Commande RemoveResource | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e2c6046-43d4-4ac1-a1b1-3795b4e44038
caps.latest.revision: "29"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d091c46ea25cbb2489264316239b6763d841a47e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="removeresource-command"></a>Commande RemoveResource
Supprime un artefact de la base de données de gestion BizTalk. L'exécution de cette commande ne supprime pas l'artefact du Global Assembly Cache (GAC), du système de fichiers, du magasin de certificats, des services Internet ou du Registre Windows s'il existe à ces emplacements. Elle ne supprime pas de définition BAM dans la base de données d'importation principale BAM ni de stratégies dans la base de données du moteur de règles. Si vous exécutez cette commande pour supprimer un fichier de liaison, les liaisons ne sont pas modifiées : seul le fichier de liaison est supprimé.  
  
 Vous pouvez utiliser cette commande pour supprimer les types d'artefact suivants :  
  
-   Assembly .NET (System.BizTalk:Assembly)  
  
-   Définition BAM (System.BizTalk:Bam)  
  
-   Assembly BizTalk (System.BizTalk:BizTalkAssembly)  
  
-   Fichier de liaison BizTalk (System.BizTalk:BizTalkBinding)  
  
-   Certificat de sécurité (System.BizTalk:Certificate)  
  
-   Composant COM (System.BizTalk:Com)  
  
-   Fichier ad hoc (System.BizTalk:File)  
  
-   Script de post-traitement (System.BizTalk:PostProcessingScript)  
  
-   Script de post-traitement (System.BizTalk:PreProcessingScript)  
  
-   Stratégie ou règle (System.BizTalk:Rules)  
  
-   Répertoire virtuel (System.BizTalk:WebDirectory)  
  
 L'opération de suppression échoue dans les cas suivants :  
  
-   tentative de suppression d'un assembly BizTalk auquel un autre assembly fait référence ;  
  
-   tentative de suppression d'un assembly BizTalk comprenant un pipeline déjà utilisé par un port d'envoi ou de réception ;  
  
-   tentative de suppression d'un assembly BizTalk comprenant un mappage déjà utilisé par un port d'envoi ;  
  
-   tentative de suppression d'un assembly BizTalk comprenant une orchestration dont l'état n'est pas « Désinscrit » ou dont une instance a été interrompue.  
  
## <a name="usage"></a>Utilisation  
 **« ApplicationName » BTSTask RemoveResource :** *valeur* **ApplicationName :** *valeur* [**/Server :**  *valeur*] [**/Database :***valeur*]  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Requis| Description|  
|---------------|--------------|-----------------|  
|**/ ApplicationName** (ou **/A**, consultez la section Notes)|Oui|Nom de l'application BizTalk contenant l'artefact de ressource à supprimer. Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («).|  
|**/ Luid** (ou **/l**, consultez la section Notes)|Oui|Identificateur unique local (LUID) de l'artefact. Vous pouvez obtenir l’identificateur LUID à l’aide de la [commande ListApp](../core/listapp-command.md).|  
|**/ Serveur** (ou **/S**, consultez la section Notes)|Non|Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.<br /><br /> Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur. Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).<br /><br /> Exemples :<br /><br /> Server=MyServer<br /><br /> Server=MyServer\MySQLServer,1533<br /><br /> Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.|  
|**/ Base de données** (ou **/D**, consultez la section Notes)|Non|Nom de la base de données de gestion BizTalk. Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.|  
  
## <a name="sample"></a>Exemple  
 **BTSTask RemoveResource /ApplicationName:MyApplication /Luid:"MyApp.Orchestrations, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = 0123456789ABCDEF »**  
  
## <a name="remarks"></a>Notes  
 Les paramètres ne respectent pas la casse. Il n'est pas nécessaire de taper le nom complet du paramètre pour l'indiquer. Vous pouvez vous contenter de taper les premières lettres du nom à condition qu'elles suffisent à identifier le paramètre sans ambiguïté.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de ligne de commande BTSTask](../core/btstask-command-line-reference.md)   
 [Comment supprimer un artefact d’une Application](../core/how-to-remove-an-artifact-from-an-application.md)