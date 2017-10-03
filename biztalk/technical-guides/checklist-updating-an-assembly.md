---
title: "Liste de vérification : Mise à jour un Assembly | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5afcb78a-333b-46ff-8681-42362ce5aaad
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9b20aa7d1b0b901176f090ab7636ef0b3eccfa9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-updating-an-assembly"></a>Liste de vérification : Mise à jour d’un Assembly
La liste de vérification suivante décrit le processus de mise à jour d’un ou plusieurs artefacts dans une application qui a déjà été déployé, puis redéployer l’application.  
  
> [!NOTE]  
>  Si vous ne peut pas planifier des temps d’arrêt ou des instances de très longue ne peut pas être terminée, mettez à jour l’à l’aide du contrôle de version côte à côte.  
  
|Étapes|Référence|  
|-----------|---------------|  
|Passez en revue les considérations importantes à prendre en compte lors de la mise à jour d'artefacts dans une application.|-   [Considérations importantes pour la mise à jour des Applications](http://go.microsoft.com/fwlink/?LinkId=154823) (http://go.microsoft.com/fwlink/?LinkId=154823).<br />-   [Meilleures pratiques pour la mise à jour des Applications](../technical-guides/best-practices-for-updating-applications.md)|  
|Vérifiez que vous disposez des autorisations adéquates pour effectuer le déploiement.|[Autorisations permettant de gérer une Application](../technical-guides/permissions-for-managing-an-application.md)|  
|Apportez les modifications nécessaires à vos assemblys, l’ajout, la suppression ou la reconfiguration des artefacts en fonction des besoins.<br /><br /> Déployer les assemblys à partir de Visual Studio dans une application BizTalk dans l’environnement de développement.|-   [Comment mettre à jour un Assembly](../technical-guides/how-to-update-an-assembly.md)<br />-   [Mise à jour d’un artefact](../technical-guides/updating-an-artifact.md)<br />-« Mise à jour d’un artefact » et « Mise à jour d’un Assembly » sections de [meilleures pratiques pour la mise à jour des Applications](../technical-guides/best-practices-for-updating-applications.md)<br />-   [Comment déployer un Assembly BizTalk à partir de Visual Studio](http://go.microsoft.com/fwlink/?LinkId=154824) (http://go.microsoft.com/fwlink/?LinkId=154824).|  
|Testez tous les artefacts nouveaux ou modifiés, en veillant à tester également tous les artefacts dépendants. **Remarque :** lors du test, veillez à prendre en compte les dépendances qui peuvent exister entre cette application et d’autres applications.|[Tâches de test pour le déploiement d’applications BizTalk](http://go.microsoft.com/fwlink/?LinkId=154825) (http://go.microsoft.com/fwlink/?LinkId=154825).|  
|Dans la console Administration de BizTalk Server, vous pouvez ajouter, supprimer ou reconfigurer les artefacts de l’application selon les besoins.|-   [Comment créer ou ajouter un artefact](http://go.microsoft.com/fwlink/?LinkID=154724) (http://go.microsoft.com/fwlink/?LinkID=154724).<br />-   [Comment supprimer un artefact d’une Application](http://go.microsoft.com/fwlink/?LinkID=154688) (http://go.microsoft.com/fwlink/?LinkID=154688).<br />-   [La gestion des artefacts](http://go.microsoft.com/fwlink/?LinkID=154725) (http://go.microsoft.com/fwlink/?LinkID=154725).<br />-   [Mise à jour d’un artefact](../technical-guides/updating-an-artifact.md)<br />-Section « Mise à jour d’un artefact » [meilleures pratiques pour la mise à jour des Applications](../technical-guides/best-practices-for-updating-applications.md).|  
|Cette commande permet d'exporter l'application contenant les artefacts nouveaux ou modifiés dans un fichier .msi.|-   [Exportation de stratégies, les liaisons et les Applications BizTalk](http://go.microsoft.com/fwlink/?LinkId=154826) (http://go.microsoft.com/fwlink/?LinkId=154826).<br />-   [Comment exporter une Application vers un fichier .msi](../technical-guides/how-to-export-an-application-to-an-msi-file.md)<br />-Section « Exportation d’une Application BizTalk » [meilleures pratiques pour le déploiement d’une Application](../technical-guides/best-practices-for-deploying-an-application.md).|  
|Si la mise à jour interfèrera avec l’application en cours d’exécution, planifier des temps d’arrêt et arrêter l’application que vous souhaitez mettre à jour.|-   [Comment démarrer et arrêter une Application BizTalk](http://go.microsoft.com/fwlink/?LinkID=154729) (http://go.microsoft.com/fwlink/?LinkID=154729).<br />-Section « Démarrer ou arrêter une Application » de [meilleures pratiques pour la mise à jour des Applications](../technical-guides/best-practices-for-updating-applications.md).|  
|Importer les artefacts modifiés ou mis à jour à partir du fichier .msi dans l’application que vous souhaitez mettre à jour, l’installation de l’application. **Remarque :** lorsque vous mettez à jour un assembly BizTalk, vous devez arrêter et désinscrire les artefacts avant d’importer à partir du fichier .msi. Vous devez inscrire de nouveau et puis démarrer les artefacts BizTalk après l’importation à partir du fichier .msi.|-   [Comment importer une Application BizTalk](http://go.microsoft.com/fwlink/?LinkId=154827) (http://go.microsoft.com/fwlink/?LinkId=154827).<br />-   [Comment importer une Application à partir d’un fichier .msi](../technical-guides/how-to-import-an-application-from-an-msi-file.md)<br />-« L’importation d’une Application BizTalk » de section de [meilleures pratiques pour le déploiement d’une Application](../technical-guides/best-practices-for-deploying-an-application.md).<br />-   [Comment installer une Application BizTalk](http://go.microsoft.com/fwlink/?LinkID=154728) (http://go.microsoft.com/fwlink/?LinkID=154728).<br />-   [Comment installer un Assembly dans le GAC](http://go.microsoft.com/fwlink/?LinkId=154828) (http://go.microsoft.com/fwlink/?LinkId=154828).|  
|Démarrez l’application, la reprise de publication des messages. Redémarrez toutes les instances d’hôte BizTalk.|-   [Comment démarrer et arrêter une Application BizTalk](http://go.microsoft.com/fwlink/?LinkID=154729) (http://go.microsoft.com/fwlink/?LinkID=154729).|  
|Si l'application vers laquelle vous importez un assembly contenant une orchestration contient déjà un assembly ayant le même nom, le même jeton de clé publique et la même version, arrêtez et redémarrez les instances de l'hôte de destination de l'orchestration. Ainsi, vous êtes sûr que la nouvelle version de l'assembly sera utilisée par BizTalk Server.|-   [Comment arrêter une Instance d’hôte](http://go.microsoft.com/fwlink/?LinkId=154829) (http://go.microsoft.com/fwlink/?LinkId=154829).<br />-   [Comment démarrer une Instance d’hôte](http://go.microsoft.com/fwlink/?LinkId=154830) (http://go.microsoft.com/fwlink/?LinkId=154830).|