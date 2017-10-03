---
title: "Que sont les intercepteurs WCF et WF BAM ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 198bfdc9-86ff-4017-b65f-19616deeb9f4
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c819d219a9796b485434101ee1c2f2d4be136ae0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-are-the-bam-wcf-and-wf-interceptors"></a>Que sont les intercepteurs WCF et WF BAM ?
Le composant d'analyse BAM (Business Activity Monitoring) est un ensemble d'outils, d'API et de services qui permet de gérer des agrégations, des alertes et des profils, et d'instrumenter des processus automatiques pour envoyer des événements en vue d'analyser les mesures de performances relatives à une activité commerciale. Ensemble, ils fournissent une visibilité de bout en bout des processus d'entreprise et permettent d'avoir une vue d'ensemble des états et résultats des processus d'entreprise.  
  
 Les intercepteurs BAM étendent ces fonctionnalités dans Windows Workflow Foundation (WF), Windows Communication Foundation (WCF) et d'autres environnements d'exécution. Ils permettent de suivre vos processus d’entreprise sans recompiler votre solution WF ou WCF (l’intégration est effectuée via un fichier de configuration).  
  
 L'utilisation de l'intercepteur WF ou WCF BAM dans un projet vous permet d'effectuer les tâches suivantes :  
  
-   utiliser le portail BAM pour consulter les informations relatives aux processus d'entreprise exécutés dans votre application WF ou WCF ;  
  
-   utiliser les fonctionnalités de l'analyse BAM sans ajouter de code à votre application ;  
  
-   déployer votre solution à l'aide d'outils et d'utilitaires BizTalk Server familiers ;  
  
-   utiliser votre environnement BizTalk Server existant pour les applications WF et WCF existantes et nouvelles.  
  
## <a name="interceptor-components"></a>Composants d'un intercepteur  
 L'ensemble de composants Common Interceptor Foundation constitue l'élément central d'un intercepteur BAM. Il fournit la base pour créer des intercepteurs personnalisés pour les environnements hétérogènes. Il inclut les composants partagés suivants :  
  
-   **BM.exe**, une version améliorée de l’utilitaire de déploiement BAM étendu pour modifier les configurations d’intercepteurs associées, y compris ajouter, supprimer, mettre à jour et fonctionnalités de liste.  
  
-   **CommonInterceptorConfiguration.xsd**, le schéma XML de configuration Common Interceptor Foundation. Les configurations des intercepteurs doivent au moins être validées par rapport à ce schéma.  
  
## <a name="windows-workflow-foundation-wf-interceptor"></a>Intercepteur Windows Workflow Foundation (WF)  
 L'intercepteur Windows Workflow Foundation permet d'ajouter de façon transparente les fonctionnalités de suivi BAM aux applications WF nouvelles et existantes. Une fois la configuration de l'intercepteur déployée dans la base de données d'importation principale BAM et les instances de l'application WF configurées pour charger l'intercepteur WF BAM, les données de flux de travail sont écrites dans l'analyse BAM, sans code supplémentaire. L'intercepteur WF présente les caractéristiques suivantes :  
  
-   s'intègre aux applications WF existantes sans modification ou recompilation du code.  
  
-   permet la détection au moment de l'exécution et prend en charge les fichiers de configuration modifiés. Si une nouvelle version du fichier de configuration d'un intercepteur est détectée, les nouvelles instances de flux de travail utilisent la nouvelle configuration tandis que les anciennes sont exécutées à l'aide de l'ancienne configuration.  
  
-   prend en charge les transactions. L'intercepteur WF conserve les éléments suivis en maintenant la cohérence avec les transactions WF. Les éléments suivis ne sont conservés qu'une fois la transaction WF et la transaction d'intercepteur exécutées.  
  
    > [!NOTE]
    >  L'intercepteur Windows Workflow ne prend pas en charge SharedConnectionWorkflowCommitWorkBatchService qui utilise la même connexion SQL pour les services de suivi et les services de persistance.  
  
    > [!NOTE]
    >  Dans BizTalk Server, l’intercepteur Windows Workflow Foundation (WF) ne fonctionnera pas avec le nouveau moteur WF dans .NET Framework 4. L’intercepteur WF continue de fonctionner dans .NET Framework 3.5 SP2.  
  
## <a name="windows-communication-foundation-wcf-interceptor"></a>Intercepteur Windows Communication Foundation (WCF)  
 L'intercepteur Windows Communication Foundation permet d'ajouter les fonctionnalités de suivi BAM à vos applications WCF. Il présente les caractéristiques suivantes :  
  
-   s'intègre aux applications WCF existantes sans modification ou recompilation du code.  
  
-   assure le suivi des messages contenus dans les appels de service WCF.  
  
-   assure le suivi des informations des messages dans les appels de service WCF.  
  
-   participe aux transactions transmises du client ou initiées en interne pour les appels de service traités.