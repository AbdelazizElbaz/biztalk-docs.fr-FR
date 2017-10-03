---
title: "Meilleures pratiques pour le déploiement d’une Application BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- best practices, deploying
- best practices, applications
- applications, best practices
- deploying, best practices
ms.assetid: 97ebf479-0dc5-4e95-b409-d3b6ad3d60d0
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3b50ff0a6e64633090e562b6ca8e3ae66eb8683
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-for-deploying-a-biztalk-application"></a>Méthodes conseillées pour déployer une application BizTalk
Cette rubrique décrit les méthodes de déploiement conseillées d'une application BizTalk.  
  
## <a name="group-related-artifacts-together-in-a-single-application"></a>Groupement d'artefacts associés dans une même application  
 Placez autant que possible les artefacts associés dans la même application BizTalk. Vous pouvez gérer et déployer les artefacts dans une seule entité, et ainsi simplifier la gestion. Vous avez la possibilité de grouper les artefacts qui prennent en charge le même processus d'entreprise ou ceux qui réalisent les mêmes fonctions au sein d'une application.  
  
## <a name="deploy-shared-artifacts-in-a-separate-application"></a>Déploiement d'artefacts partagés dans une application distincte  
 Si les artefacts doivent être partagés par plusieurs applications, déployez-les dans une application distincte. Si, par exemple, deux applications partagent le même schéma, placez ce dernier dans une application distincte. En effet, un seul artefact possédant le même identificateur unique local (LUID), composé du nom de l'artefact et éventuellement d'autres attributs, peut exister dans un groupe BizTalk. Si vous incluez un artefact dans une application, puis que vous créez une référence vers celui-ci à partir d'une autre application, vous risquez de rencontrer des problèmes comme un mauvais fonctionnement de cette dernière lorsque vous arrêtez l'application contenant l'artefact.  
  
 La méthode conseillée s'applique à tous les types d'artefact sauf pour les fichiers, comme les fichiers Readme (Lisezmoi) et les scripts, qui sont ajoutés à l'application en tant que type Fichier d'artefact, car plusieurs artefacts de fichier portant le même nom peuvent être déployés dans un groupe BizTalk. Vous pouvez par conséquent utiliser un fichier ayant le même nom dans plusieurs applications. L'arrêt d'une application n'aura aucune incidence sur les autres applications. Pour plus d’informations sur l’ajout d’artefacts d’un fichier, consultez [l’ajout d’un fichier à une Application](../core/how-to-add-a-file-to-an-application.md).  
  
 Pour connaître les méthodes conseillées de partage de types particuliers d'artefacts, voir les sections « Déploiement de site Web partagé dans une application distincte », « Déploiement de stratégies partagées dans une application distincte » et « Déploiement de certificats partagés dans une application distincte » de cette rubrique.  
  
## <a name="deploy-a-shared-web-site-in-a-separate-application"></a>Déploiement de site Web partagé dans une application distincte  
 Si plusieurs solutions d'entreprise doivent se partager un même site Web, déployez ce dernier dans une application distincte. En effet, lorsque vous désinstallez une application BizTalk, le répertoire virtuel du site Web qui fait partie de l'application est supprimé, même si le site est en cours d'exécution. Et si le site Web est partagé avec une autre solution d'entreprise, cette dernière ne fonctionnera plus correctement.  
  
## <a name="deploy-shared-policies-in-a-separate-application"></a>Déploiement de stratégies partagées dans une application distincte  
 Si plusieurs applications utilisent la même stratégie, vous devez la déployer dans une application distincte plutôt que de créer une référence d'une application à l'autre, car lorsque vous arrêtez une application, ses stratégies ne sont plus déployées. Si vous arrêtez une application contenant une stratégie utilisée par une autre application, la stratégie ne fonctionnera plus dans l'application.  
  
## <a name="deploy-shared-certificates-in-a-separate-application"></a>Déploiement de certificats partagés dans une application distincte  
 Si vous utilisez un certificat sur un port d'envoi ou un emplacement de réception dans plusieurs applications, vous devez déployer le certificat dans une application distincte, puis référencer cette application depuis les autres applications qui utilisent le certificat, car il ne peut exister qu'un seul artefact ayant un LUID donné dans un groupe BizTalk. Par conséquent, il est impossible d'importer le même certificat dans différentes applications. Si vous tentez d'importer deux applications utilisant le même certificat, la première importation réussira, la seconde non. Dans ce cas, l'utilisation de l'option d'importation Remplacer ne résout pas le problème, étant donné que le certificat que vous souhaitez remplacer existe dans une autre application.  
  
## <a name="never-deploy-an-assembly-from-visual-studio-on-a-production-computer"></a>Ne jamais déployer un assembly de Visual Studio sur un ordinateur de production  
 En phase de développement, les développeurs redéploient souvent les assemblys à partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Pour activer le redéploiement, [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] peut annuler le déploiement, supprimer la liaison, arrêter et désinscrire les artefacts inclus dans les assemblys. Bien que tout ceci soit nécessaire et approprié à l'environnement de développement, cela peut entraîner des conséquences inattendues et indésirables dans l'environnement de production. C'est pourquoi, afin d'éviter qu'une personne ne tente de déployer un assembly à partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] sur un ordinateur de production, il est déconseillé d'installer [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] sur les ordinateurs de production.  
  
 En outre, ne faites jamais référence à une base de données de production à partir d'un ordinateur exécutant [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
## <a name="when-deploying-large-msi-files-you-may-need-to-increase-the-default-transaction-timeout-of-the-com-components-used-by-biztalk-to-deploy-applications"></a>Lors du déploiement de fichiers MSI volumineux, vous pouvez avoir besoin d'augmenter le délai d'expiration de transaction par défaut des composants COM+ utilisés par BizTalk pour déployer les applications.  
 Si le fichier MSI déployé est supérieur à 100 Mo, l'application ne sera probablement pas déployée dans le délai d'expiration de transaction par défaut des composants COM+ utilisés par BizTalk au cours du déploiement. Si les transactions associées à ces composants COM+ expirent avant la fin du déploiement, ce dernier échoue. Si vous déployez des fichiers MSI vraiment volumineux, envisagez d'utiliser une de ces méthodes pour limiter le problème :  
  
1.  Déployez plusieurs fichiers MSI plus petits, plutôt qu'un seul fichier MSI volumineux.  
  
2.  Augmenter le délai d’expiration de transaction par défaut de 3 000 secondes associé à la **Microsoft.BizTalk.ApplicationDeployment.Group** et **Microsoft.BizTalk.Deployment.DeployerComponent** composants dans le **Services de composants** interface de gestion. Ces composants appartiennent à la **Microsoft.BizTalk.ApplicationDeployment.Engine** et **Microsoft.Biztalk.Deployment** applications COM + respectivement. Pour plus d’informations sur la modification de la transaction de valeur de délai d’expiration pour un composant COM + voir [comment modifier la valeur de délai d’attente de Transaction pour MTS ou COM +](http://go.microsoft.com/fwlink/?LinkId=67691).  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement et gestion des Applications BizTalk](../core/deploying-and-managing-biztalk-applications.md)