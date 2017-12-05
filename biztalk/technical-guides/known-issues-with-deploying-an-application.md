---
title: "Problèmes connus avec le déploiement d’une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e5fb4f6-f9bd-4322-93f9-723e9e3c3317
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b7fa139469ea8718c3d4430235ffb576195e67a7
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="known-issues-with-deploying-an-application"></a>Problèmes connus avec le déploiement d’une Application
## <a name="deploying-a-biztalk-application"></a>Déploiement d’une Application BizTalk  
 **Déployer une application de mises à jour, correction des références**  
  
 Si vous déployez une toute nouvelle application en remplacement de l'application existante, vous devez corriger toutes les références entre les autres applications et l'application que vous remplacez.  
  
 **À l’aide de Visual Studio pour déployer une application peut s’arrêter des applications**  
  
> [!NOTE]  
>  Nous vous recommandons d’éviter à l’aide de Visual Studio pour déployer une application dans un environnement de production.  
  
 Si vous utilisez Visual Studio pour déployer une application dans un environnement de production et de l’option redémarrer les Instances d’hôte est défini sur True dans les propriétés du projet, toutes les instances de l’hôte redémarre lorsque vous déployez l’application, y compris ceux qui ne sont pas associés Cette application. Ce processus interrompra toutes les autres applications exécutées sur les instances d'hôte de l'ordinateur local.  
  
## <a name="adding-artifacts-to-a-biztalk-application"></a>Ajout d’artefacts à une Application BizTalk  
 **Déplacement d’un artefact peut déplacer des dépendances**  
  
 Lorsque vous déplacez un artefact vers une nouvelle application, tous les artefacts sur lequel il possède des dépendances sont également déplacés, sauf si la nouvelle application comporte une référence à l’ou les applications contenant les artefacts dont dépend de l’artefact déplacé. En outre, tous les artefacts ayant des dépendances sur l’artefact déplacé également seront déplacés, sauf si les applications les contenant comportent une référence à la nouvelle application. Lors du déplacement d'un artefact, la liste des ceux qui seront également déplacés s'affiche. Pour obtenir des instructions sur le déplacement d’un artefact, voir [comment déplacer un artefact vers une autre Application](http://go.microsoft.com/fwlink/?LinkId=154999) (http://go.microsoft.com/fwlink/?LinkId=154999).  
  
## <a name="exporting-a-biztalk-application"></a>Exportation d’une Application BizTalk  
 **Une erreur incorrecte peut s’afficher lors de l’installation d’un fichier .msi sur Windows Vista**  
  
 Lorsque vous installez un package .msi exporté à l’aide de [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] sur BizTalk Server s’exécutant sur Windows Vista®, vous pouvez recevoir l’erreur incorrecte suivante, « le programme d’installation a rencontré une erreur inattendue, l’installation de ce package. Il s'agit peut-être d'un problème lié au package. Le code d'erreur est 2869. ». Pour corriger cette erreur, d’abord importer le package à l’aide de BizTalk Server et puis ré-exportez et installer le package.  
  
## <a name="importing-a-biztalk-application"></a>L’importation d’une Application BizTalk  
 **Les mots de passe ne sont pas supprimés à partir de fichiers ajoutés à l’application de liaison**  
  
 Pour des raisons de sécurité, pendant l'exportation d'une application, les mots de passe sont supprimés des liaisons d'application. Néanmoins, ils ne sont pas supprimés des fichiers de liaison ajoutés à l'application. Après avoir importé l'application, vous devez reconfigurer les mots de passe afin que l'application fonctionne correctement. Faire cela en modifiant le fichier de liaison ou à l’aide de la console d’Administration. Pour plus d’informations sur la modification d’un fichier de liaison, consultez [personnalisation des fichiers de liaison](http://go.microsoft.com/fwlink/?LinkId=155000) (http://go.microsoft.com/fwlink/?LinkId=155000). Pour plus d’informations sur la configuration de la sécurité pour les adaptateurs, consultez [à l’aide des adaptateurs](http://go.microsoft.com/fwlink/?LinkId=155001) (http://go.microsoft.com/fwlink/?LinkId=155001).  
  
 **BizTalk Server ne restaure pas les importations sous forme de script ou installations**  
  
 Si une importation échoue, BizTalk Server annule toutes les opérations d'importation sauf pour les actions effectuées par des scripts personnalisés. Cela est également vrai pour installer et désinstaller des opérations.  
  
 **Un schéma manquant ne peut pas être signalé après une importation**  
  
 Si vous créez un filtre pour un port d'envoi dans une application qui utilise un schéma de propriété d'une autre application et que vous importiez ensuite la première application dans un nouveau groupe BizTalk, vous ne recevrez pas de message vous avertissant de l'absence de schéma et le filtrage ne fonctionnera pas une fois l'application installée et démarrée. Vous pouvez corriger ce problème en important l'application qui contient le schéma avant d'installer l'application sans schéma.  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement d’une application](../technical-guides/deploying-an-application.md)