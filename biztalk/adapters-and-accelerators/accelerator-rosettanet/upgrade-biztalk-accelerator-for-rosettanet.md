---
title: "Mise à niveau de BizTalk Accelerator pour RosettaNet (BTARN) dans BizTalk Server | Documents Microsoft »"
description: "Suivez les étapes de mise à niveau pour mettre à jour BTARN vers la version actuelle de BizTalk Server"
author: MandiOhlinger
manager: anneta
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
ms.author: mandia
ms.openlocfilehash: 16e6083f3e5fb1778d77536cd602ee2208c0005f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="upgrade-the-rosettanet-accelerator"></a>Mise à niveau de l’accélérateur RosettaNet

## <a name="upgrade-overview"></a>Vue d’ensemble de la mise à niveau
Vous pouvez mettre à niveau la version précédente de BizTalk Accelerator pour l’installation de RosettaNet (BTARN) vers la version actuelle. Le processus de mise à niveau implique la mise à niveau de BizTalk Server et puis mise à niveau de BTARN.  
  
 Vous pouvez mettre à niveau à partir de la version précédente de BTARN à un en exécutant le programme d’installation de BTARN. Le programme d’installation migre les informations de configuration de BTRAN vers la version actuelle.  
  
 Dans un environnement de BTARN multiserveur, vous devez mettre à niveau tous les serveurs BizTalk tout d’abord, puis à BTARN. Migrez vos serveur dans l'ordre suivant :  
  
-   Le serveur hébergeant le groupe BizTalk  
  
-   Chaque nœud de traitement  
  
-   Le serveur du portail BAM  
  
 Dans la BTARN mise à niveau, assurez-vous de que procéder comme suit :  
  
-   Vérifiez que le service SQL Server (MSSQLSERVER) est en cours d'exécution.  
  
-   N'exécutez pas une installation sans assistance.  
  
## <a name="upgrade-steps"></a>Étapes de la mise à niveau  
  
1.  Mise à niveau de BizTalk Server. Consultez [BizTalk Server quelles sont les nouveautés, Installation, Configuration et mise à niveau](../../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).
  
2.  Sauvegardez la base de données BTARN et les schémas de message BTARN.  
  
    > [!NOTE]
    >  Vous devez sauvegarder la base de données BTARN pour des raisons de sécurité. Le programme d’installation migre la base de données BTRAN vers une version plus récente.  
  
3.  Sauvegardez tous les fichiers sous le *< lecteur\>*: \Program Files\\Microsoft BizTalk Accelerator pour RosettaNet dossier que vous avez apporté des modifications, par exemple, les fichiers dans le Kit de développement.  
  
4.  Annulez le déploiement des projets ou assemblys qui contiennent des références à une ou plusieurs versions des assemblys de BTARN.  
  
5.  Dans Visual Studio, annulez manuellement le déploiement de tous les assemblys BTARN, dans l’ordre suivant :  
  
    -   Microsoft.Solutions.BTARN.CommonTypes  
  
    -   Microsoft.Solutions.BTARN.GlobalSchemas  
  
    -   Microsoft.Solutions.BTARN.PipelineReceive  
  
    -   Microsoft.Solutions.BTARN.PipelineSend  
  
    -   Microsoft.Solutions.BTARN.PrivateInitiator  
  
    -   Microsoft.Solutions.BTARN.PrivateResponder  
  
    -   Microsoft.Solutions.BTARN.PublicInitiator  
  
    -   Microsoft.Solutions.BTARN.PublicResponder  
  
    -   Microsoft.Solutions.BTARN.Schemas.RNIFv11  
  
    -   Microsoft.Solutions.BTARN.Schemas.RNIFv20  
  
    -   Microsoft.Solutions.BTARN.Schemas.RNPIPs  
  
6.  Exécutez l’installation de BTARN. Consultez [installer et configurer l’accélérateur RosettaNet](install-configure-biztalk-accelerator-for-rosettanet.md).
  
7.  Utilisez **BTSTask.exe** (\Program Files\Microsoft BizTalk Server) à redéployer manuellement les assemblys BTARN dans l’ordre suivant :  
  
    -   Microsoft.Solutions.BTARN.CommonTypes  
  
    -   Microsoft.Solutions.BTARN.GlobalSchemas  
  
    -   Microsoft.Solutions.BTARN.PipelineReceive  
  
    -   Microsoft.Solutions.BTARN.PipelineSend  
  
    -   Microsoft.Solutions.BTARN.PrivateInitiator  
  
    -   Microsoft.Solutions.BTARN.PrivateResponder  
  
    -   Microsoft.Solutions.BTARN.PublicInitiator  
  
    -   Microsoft.Solutions.BTARN.PublicResponder  
  
    -   Microsoft.Solutions.BTARN.Schemas.RNIFv11  
  
    -   Microsoft.Solutions.BTARN.Schemas.RNIFv20  
  
    -   Microsoft.Solutions.BTARN.Schemas.RNPIPs  
  
    > [!NOTE]
    >  Pour plus d’informations sur **BTSTask.exe**, consultez la rubrique « Référence de ligne de commande BTSTask » dans l’aide de BizTalk Server.  
  
8.  Regénérez les projets ou les assemblys qui contiennent une référence à un ou plusieurs des [assemblys BTARN. Utilisez **BTSTask.exe** à redéployer manuellement ces projets.  
  
9. Mettez à niveau les dossiers virtuels dans IIS à partir de ASP.NET 2.0 vers ASP.NET 4.0 pour ce qui suit :  
  
    -   BTARNApp  
  
    -   BTARNHttpReceive  
  
10. Redémarrez l'ordinateur pour appliquer les modifications éventuellement effectuées.  
  
