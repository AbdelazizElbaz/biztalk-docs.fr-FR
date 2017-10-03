---
title: "Gérer le portail BAM dans BizTalk Server | Documents Microsoft"
Description: "Vue d’ensemble de l’installation et la configuration du portail BAM dans BizTalk Server"
ms.custom: 
ms.date: 08/15/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a08aa85-3a45-4a8c-bdb5-5615ca097ce1
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d7908c9c7ce8e4b731e0b88569e3dc3fb228a1d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manage-the-bam-portal"></a>Gérer le portail BAM

## <a name="set-up-bam-portal"></a>Configurer le portail BAM
En tant qu'administrateur, vous pouvez configurer le portail BAM en exécutant le programme d'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Les outils de configuration de BizTalk Server permettent d'indiquer si le composant BAM est activé, de spécifier les comptes de service Web, les groupes Windows autorisés à afficher le portail ainsi que le site Web destiné à héberger ce portail. Lorsqu'il s'avère nécessaire de mettre à jour la configuration du portail BAM après l'avoir installé, utilisez l'outil de configuration afin de mettre à jour les paramètres tels que le groupe d'utilisateurs du portail, le compte du pool d'applications et l'utilisateur des services Web de gestion.  
  
 Pour plus d’informations sur l’installation du portail BAM, consultez [Install and Configure le BAM dans plusieurs environnements d’ordinateur](http://social.technet.microsoft.com/wiki/contents/articles/1888.install-and-configure-bam-business-activity-monitoring-in-a-multi-computer-environment.aspx).  
  
 Pour plus d’informations sur la configuration du portail BAM, consultez [configurer BizTalk Server](../install-and-config-guides/configure-biztalk-server.md).
  
 Le portail BAM est doté de nombreux paramètres personnalisables par modification du fichier webconfig.xml. Ces paramètres permettent de contrôler les performances et le fonctionnement du portail. Le reste de cette section décrit la procédure de personnalisation de la configuration de votre portail BAM.  
  
## <a name="next-steps"></a>Étapes suivantes 
  
-   [Personnalisation de la Configuration du portail BAM](../core/customizing-the-bam-portal-configuration.md)  
  
-   [Comment configurer le portail BAM pour travailler sur un Cluster d’équilibrage de charge réseau](../core/how-to-configure-the-bam-portal-to-work-on-an-nlb-cluster.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md)