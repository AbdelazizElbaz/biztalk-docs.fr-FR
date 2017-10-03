---
title: "Développer des applications Siebel à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF service model, developing applications by using
- WCF service model, performing operations
- proxy programming, performing operations
- WCF service model, advantages of using
ms.assetid: df5627b9-c80d-4a75-a20a-a0be119735a2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c14560fb92eb2cca1e55d32e556dec23725a0de6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="develop-siebel-applications-using-the-wcf-service-model"></a>Développer des applications Siebel à l’aide du modèle de Service WCF
[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]fournit un modèle de programmation appelé le modèle de service WCF, ce qui permet en partie, certaines des limitations d’un autre modèle de programmation, le modèle de canal WCF.  
  
 Niveau le plus bas, le [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] présente le modèle de canal WCF dans lequel les clients pour appeler les opérations sur un service en échangeant des messages SOAP sur un canal établi entre les points de terminaison de client et le service. Le modèle de canal WCF expose les types de données et des méthodes qui permettent d’agir directement sur l’architecture de canal WCF. Le modèle de canal WCF vous offre un contrôle direct sur le contenu des messages SOAP que vous créez et de façon à la fois votre application et le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] les utiliser. Toutefois, des messages SOAP correct à envoyer via un canal de création et valider les messages de réponse retournés peuvent s’avérer détaillées et précises.  
  
 Le modèle de service WCF, toutefois, implique l’utilisation des classes proxy pour appeler des opérations sur un service cible ou de recevoir des opérations à partir d’un client. Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] expose le système Siebel comme service WCF sur lequel vous pouvez appeler des opérations.  
  
-   La classe proxy utilisée pour appeler des opérations sur un service cible est appelée une classe de client WCF. Cette classe modélise les opérations exposées par un service en tant que méthodes .NET avec des paramètres fortement typés. À l’aide du modèle de service WCF, vous pouvez appeler les opérations exposées par le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] en tant que méthodes .NET sur le client WCF. Pour plus d’informations sur les clients WCF, consultez [vue d’ensemble du Client WCF](https://msdn.microsoft.com/library/ms735103.aspx).   
  
 Vous utilisez des outils pour générer une classe de client WCF et code d’assistance à partir des métadonnées de service associé qui le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] expose. Vous pouvez utiliser un des outils suivants :  
  
-   Le service Model Metadata Utility Tool (svcutil.exe), qui est fourni avec WCF  
  
-   Le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], qui est fourni avec le[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]  
  
 Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] est intégré à la [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] l’expérience de conception et présente un Microsoft Windows standard de l’interface qui fournit puissants de parcourir et de recherche avancées sur les opérations exposées par l’adaptateur. Pour plus d’informations sur la façon de générer un client WCF, consultez [générer un Client WCF ou un contrat de service WCF pour Siebel solution artefacts](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md)  
  
## <a name="why-choose-the-wcf-service-model-or-the-wcf-channel-model"></a>Pourquoi choisir le modèle de Service WCF ou le modèle de canal WCF ?  
 Car il présente un modèle qui est familier aux programmeurs .NET et masque la complexité sous-jacente d’échange de messages SOAP sur un canal, le modèle de service WCF est souvent le meilleur choix pour développer des solutions de programmation pour le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]. Toutefois, il existe des scénarios dans lesquels le modèle de canal WCF peut être un meilleur choix. Par exemple, sérialisation et désérialisation entre la représentation XML d’objets dans un message SOAP et les types .NET utilisés pour représenter dans le modèle de service WCF impliquent la lecture de la totalité du message en mémoire.  
  
 Le modèle de canal WCF prend en charge la diffusion en continu au niveau du nœud XML sur toutes les opérations. Dans le niveau de nœud de diffusion en continu, uniquement à chaque nœud du message XML est conservée en mémoire à tout moment. Pour certaines opérations, par exemple, si vous effectuez des requêtes qui retournent des jeux de résultats volumineux, le modèle de canal WCF peut être un meilleur choix pour votre application. Pour plus d’informations sur l’utilisation du modèle de canal WCF, consultez [développer les Applications Siebel à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-channel-model3.md).  
  
 Les rubriques de cette section contiennent des informations, des procédures et des exemples pour vous aider à créer et utiliser le modèle de service WCF pour développer des applications à l’aide de la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Vue d’ensemble du modèle de Service WCF avec l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/overview-of-the-wcf-service-model-with-the-siebel-adapter.md)  
  
-   [Métadonnées et le modèle de Service WCF avec Siebel](../../adapters-and-accelerators/adapter-siebel/metadata-and-the-wcf-service-model-with-siebel.md)  
  
-   [Générer un Client WCF ou un contrat de service WCF pour Siebel solution artefacts](../../adapters-and-accelerators/adapter-siebel/generate-a-wcf-client-or-a-wcf-service-contract-for-siebel-solution-artifacts.md)  
  
-   [Configurer un Client WCF pour un système Siebel](../../adapters-and-accelerators/adapter-siebel/configure-a-wcf-client-for-a-siebel-system.md)  
  
-   [Exécuter des opérations sur les composants d’entreprise avec l’adaptateur Siebel à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-with-the-siebel-adapter-using-wcf-service.md)  
  
-   [Exécuter des opérations sur les composants d’entreprise avec des champs de groupe à valeurs multiples avec l’adaptateur Siebel à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-siebel/work-with-mvp-fields-using-the-siebel-adapter-and-the-wcf-service-model.md)  
  
-   [Appeler des méthodes de Service d’entreprise avec l’adaptateur Siebel à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-siebel/run-business-service-methods-with-the-siebel-adapter-using-a-wcf-service.md)  
  
## <a name="see-also"></a>Voir aussi  
[Développer vos applications Siebel](../../adapters-and-accelerators/adapter-siebel/develop-your-siebel-applications.md)