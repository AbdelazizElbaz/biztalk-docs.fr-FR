---
title: "Exemple d’Architecture : Adaptateur de fichier | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, security
- architecture, examples
- File adapters, security
- security, examples
- security, architecture
- examples, architecture
- architecture, security
- File adapters, architecture examples
ms.assetid: fdcbba0c-e301-46ce-8940-d617232cafbd
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 11884786f743ece21a8009ea339a251b107420c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sample-architecture-file-adapter"></a>Exemple d’Architecture : Adaptateur de fichier
Cette rubrique décrit l'exemple d'architecture associé à l'utilisation de l'adaptateur FILE pour échanger des messages.  
  
## <a name="file-adapter-components"></a>Composants de l'adaptateur FILE  
 La figure suivante illustre les composants de l'exemple d'architecture BizTalk Server associé à l'utilisation de l'adaptateur FILE.  
  
> [!NOTE]
>  Cet exemple d'architecture s'applique également à l'adaptateur EDI.  
  
 **Figure 1 exemple d’architecture qui affiche l’adaptateur File**  
  
 ![Exemple d’architecture pour l’adaptateur File](../core/media/tdi-sec-refarch-file.gif "TDI_Sec_RefArch_File")  
  
 Cet exemple d’architecture contient les composants décrits dans les sections suivantes.  
  
## <a name="perimeter-network-internet"></a>Internet de réseau de périmètre  
 Les entreprises utilisent généralement le protocole FILE pour les communications basées sur intranet, de sorte que vous n'avez pas besoin de serveurs dans le réseau de périmètre Internet pour prendre en charge ce scénario.  
  
## <a name="perimeter-network-intranet"></a>Réseau de périmètre-intranet  
 Lorsque vous utilisez l'adaptateur FILE, un serveur FILE est présent dans le réseau de périmètre intranet. Il s'agit du serveur dans lequel les partenaires déposent leurs messages et l'adaptateur de réception FILE de BizTalk récupère les messages.  
  
## <a name="e-business-domain"></a>Domaine E-Business  
 Les serveurs de ce domaine sont les suivants :  
  
-   **BizTalk Server (traitement, adaptateur de fichier et les hôtes de suivi).** Le moteur d'exécution BizTalk Server est installé sur ce serveur, ainsi que les instances des hôtes qui contiennent les orchestrations, les pipelines, le Moteur de règles d'entreprise et les autres processus d'entreprise de BizTalk Server. C'est là que les ports, emplacements de réception, pipelines, mappages, schémas et assemblys de BizTalk Server se trouvent pour recevoir, router, traiter et envoyer des messages. Ce serveur dispose également d'une instance d'hôte qui prend en charge le suivi des données d'analyse du fonctionnement et de l'entreprise. En outre, cet hôte contient les instances de l'hôte qui exécute les adaptateurs d'envoi et de réception FILE.  
  
    > [!NOTE]
    >  Plus ces besoins augmentent, plus vous pouvez ajouter de serveurs BizTalk Server à votre environnement pour les instances de vos hôtes de traitement. Pour plus d’informations sur la configuration de BizTalk Server pour la haute disponibilité, consultez [planification pour une haute disponibilité](../core/planning-for-high-availability3.md).  
  
-   **Serveur de secret principal.** Identique à la [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).  
  
-   **SQL Server.** Identique à la [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).  
  
-   **Contrôleur de domaine.** Identique à la [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).  
  
-   **Outils d’administration.** Identique à la [exemple d’Architecture : BizTalk Server de Base](../core/sample-architecture-base-biztalk-server.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’architecture pour les petites et moyennes entreprises](../core/sample-architectures-for-small-medium-sized-companies.md)   
 [Exemples de scénarios d’analyse du modèle](../core/sample-scenarios-for-threat-model-analysis.md)