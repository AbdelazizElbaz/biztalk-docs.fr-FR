---
title: Développer des applications SAP à l’aide du modèle de Service WCF | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF service model, developing applications
ms.assetid: 5387d063-31d3-49b3-9771-354802542f8f
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4933610f8416b2c7fb81861562480e355dd8d373
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="develop-sap-applications-using-the-wcf-service-model"></a>Développer des applications SAP à l’aide du modèle de Service WCF
Niveau le plus bas, la [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] présente un modèle de programmation dans lequel les clients pour appeler les opérations sur un service en échangeant des messages SOAP sur un canal établi entre les points de terminaison de client et le service. Ce modèle, appelé le modèle de canal WCF, expose les types de données et des méthodes qui permettent d’agir directement sur l’architecture de canal WCF. Le modèle de canal WCF vous offre un contrôle direct sur le contenu des messages SOAP que vous créez et de façon à la fois votre application et le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] consommer ; Toutefois, en créant des messages SOAP correct à envoyer via un canal et en validant le les messages de réponse retournés peuvent être une tâche détaillée et précises.  
  
 Pour cette raison, [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] fournit un autre modèle de programmation appelé le modèle de service WCF. Le modèle de service WCF implique l’utilisation des classes proxy pour appeler des opérations sur un service cible ou de recevoir des opérations à partir d’un client.  
  
-   La classe proxy utilisée pour appeler des opérations sur un service cible est appelée une classe de client WCF. Cette classe modélise les opérations exposées par un service en tant que méthodes .NET avec des paramètres fortement typés. À l’aide du modèle de service WCF, vous pouvez appeler les opérations exposées par le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] en tant que méthodes .NET sur le client WCF. Pour plus d’informations sur les clients WCF, consultez [vue d’ensemble du Client WCF](https://msdn.microsoft.com/library/ms735103.aspx).
  
-   La classe proxy utilisée pour une opération de réception à partir d’un client est appelée une classe de contrat de service WCF. Cette classe modélise une opération exposée par votre code comme une méthode de rappel avec des paramètres fortement typés. Vous pouvez héberger ensuite une instance de cette classe dans un **System.ServiceModel.ServiceHost** pour permettre à un client d’appeler l’opération sur votre code. En utilisant le modèle de service WCF et d’une classe de contrat de service WCF ciblé à l’opération POLLINGSTMT, vous pouvez recevoir les résultats d’une requête d’interrogation de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
 Vous utilisez des outils pour générer une classe de client WCF ou un contrat de service WCF et code d’assistance à partir des métadonnées de service associé qui le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] expose. Vous pouvez utiliser un des outils suivants :  
  
-   Le service Model Metadata Utility Tool (svcutil.exe), qui est fourni avec WCF  
  
-   Le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], qui est fourni avec le[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]  
  
 Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] est intégré à la [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] l’expérience de conception et présente un Microsoft Windows standard de l’interface qui fournit puissants de parcourir et de recherche avancées sur les opérations exposées par l’adaptateur. Pour plus d’informations sur la façon de générer un client WCF ou une classe de contrat de service WCF, consultez [générer un Client WCF ou un contrat de Service WCF pour la solution SAP artefacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).  
  
 Car il présente un modèle qui est familier aux programmeurs .NET et qui masque la complexité sous-jacente d’échange de messages SOAP sur un canal, le modèle de service WCF est souvent le meilleur choix pour développer des solutions de programmation pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Toutefois, il existe des scénarios dans lesquels le modèle de canal WCF peut être un meilleur choix ; les scénarios en particulier dans le flux est important. C’est parce que la sérialisation et désérialisation entre la représentation XML d’objets dans un message SOAP et les types .NET utilisés pour représenter dans le modèle de service implique la lecture de la totalité du message en mémoire. Pour plus d’informations sur l’utilisation du modèle de canal WCF, consultez [applications SAP de développer à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md).
  
 Les rubriques de cette section contiennent des informations, des procédures et des exemples pour vous aider à créer et utiliser le modèle de service WCF pour développer des applications à l’aide de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Vue d’ensemble du modèle de Service WCF avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/overview-of-the-wcf-service-model-with-the-sap-adapter.md)  
  
-   [Métadonnées et le modèle de Service WCF avec SAP](../../adapters-and-accelerators/adapter-sap/metadata-and-the-wcf-service-model-with-sap.md)  
  
-   [Génération d’un Client WCF ou un contrat de Service WCF pour la solution SAP artefacts](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md)  
  
-   [Configurer une liaison de Client pour le système SAP](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md)  
  
-   [Appeler les RFC dans SAP à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-the-wcf-service-model.md)  
  
-   [Recevoir des appels entrants RFC dans SAP à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-in-sap-using-the-wcf-service-model.md)  
  
-   [Appeler tRFCs en utilisant le modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-the-wcf-service-model.md)  
  
-   [Réception entrant tRFC appelle dans SAP à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/receive-inbound-trfc-calls-in-sap-using-the-wcf-service-model.md)  
  
-   [Appeler des interfaces BAPI dans SAP à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/invoke-bapis-in-sap-using-the-wcf-service-model.md)  
  
-   [Envoyer des IDOC à SAP à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/send-idocs-to-sap-using-the-wcf-service-model.md)