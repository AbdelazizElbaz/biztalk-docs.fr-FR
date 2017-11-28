---
title: La Configuration de journalisation | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, auditing
- configuring, logging
- logging, configuring
- auditing, configuring
ms.assetid: 5cd7aec1-bd38-4d37-9a79-b01eeb89337d
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 058a1fce8105a3147fb2e537a9182e7d886bb953
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="logging-configuration"></a><span data-ttu-id="35223-102">Configuration de journalisation</span><span class="sxs-lookup"><span data-stu-id="35223-102">Logging Configuration</span></span>
<span data-ttu-id="35223-103">Ensemble, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] et [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] offrent numérique transactionnelles et d’intégration d’Application d’entreprise (IAE) des communications sécurisées pour les fournisseurs de soins de santé telles que nombre, ateliers et soins particuliers.</span><span class="sxs-lookup"><span data-stu-id="35223-103">Together, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] and [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] offer secure transactional and digital Enterprise Application Integration (EAI) communications for health care providers such as hospitals, clinics, and nursing homes.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="35223-104">permet de coordonner l’activité d’application et traitement des transactions, router des messages de manière dynamique, valider et transformer des données et le transport via une variété de cartes.</span><span class="sxs-lookup"><span data-stu-id="35223-104"> provides the ability to coordinate application activity and transaction processing, dynamically route messages, validate and transform data, and transport over a variety of adapters.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="35223-105">prend en charge l’American National Standards Institute ANSI-accredited d’intégrité au niveau sept (HL7) standard utilisé par les applications cliniques et d’administration dans les réseaux de fournisseur pour échanger des données médicales en temps réel de la messagerie.</span><span class="sxs-lookup"><span data-stu-id="35223-105"> supports the American National Standards Institute (ANSI)-accredited Health Level Seven (HL7) messaging standard used by clinical and administrative applications in provider networks to exchange medical data in real-time.</span></span>  
  
 <span data-ttu-id="35223-106">Les messages HL7 qui passent par le système d’accélérateur peuvent être très critiques.</span><span class="sxs-lookup"><span data-stu-id="35223-106">The HL7 messages that pass through the accelerator system can be very critical.</span></span> <span data-ttu-id="35223-107">Par exemple, les données pourraient être médical du patient ou une transaction financière.</span><span class="sxs-lookup"><span data-stu-id="35223-107">For example, the data could be a patient's medical record or a financial transaction.</span></span> <span data-ttu-id="35223-108">Pour assurer la conformité avec HL7 de sécurité et de confidentialité, les administrateurs système doivent être en mesure d’effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="35223-108">To ensure compliance with HL7 security and privacy regulations, system administrators must be able to do the following:</span></span>  
  
-   <span data-ttu-id="35223-109">Déboguer des messages suspendus</span><span class="sxs-lookup"><span data-stu-id="35223-109">Debug suspended messages</span></span>  
  
-   <span data-ttu-id="35223-110">Surveiller l’accès en continu pour détecter les intrus potentiels et de réduire le risque de failles de sécurité système et de fichier</span><span class="sxs-lookup"><span data-stu-id="35223-110">Monitor system and file access on an ongoing basis to detect potential intruders and reduce the risk of security breaches</span></span>  
  
 <span data-ttu-id="35223-111">Cette section fournit des informations conceptuelles et des procédures vous permettent de configurer l’audit et la journalisation, examiner et interpréter les données d’audit et journaux des événements et exécuter des requêtes sur les données enregistrées.</span><span class="sxs-lookup"><span data-stu-id="35223-111">This section provides conceptual and procedural information to enable you to configure auditing and logging, examine and interpret audit data and event logs, and run queries against the logged data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="35223-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="35223-112">In This Section</span></span>  
  
-   [<span data-ttu-id="35223-113">Sur le processus d’enregistrement</span><span class="sxs-lookup"><span data-stu-id="35223-113">About the Logging Process</span></span>](../../adapters-and-accelerators/accelerator-hl7/about-the-logging-process.md)  
  
-   [<span data-ttu-id="35223-114">Configuration de la journalisation</span><span class="sxs-lookup"><span data-stu-id="35223-114">Configuring Logging</span></span>](../../adapters-and-accelerators/accelerator-hl7/configuring-logging.md)