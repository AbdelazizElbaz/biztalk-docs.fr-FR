---
title: "Les paramètres de Configuration de l’accusé de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- acknowledgements, configuring
- configuring, acknowledgements
ms.assetid: 46e92560-7b1e-4d53-9de8-8ded4de90695
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93dea42fd084f22b4644f0acbb21860d69f75027
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ack-configuration-settings"></a><span data-ttu-id="d27da-102">Paramètres de Configuration de l’accusé de réception</span><span class="sxs-lookup"><span data-stu-id="d27da-102">ACK Configuration Settings</span></span>
<span data-ttu-id="d27da-103">Le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] analyseur génère des accusés de réception en fonction des paramètres de gestion des partenaires commerciaux (GPC).</span><span class="sxs-lookup"><span data-stu-id="d27da-103">The [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] parser generates acknowledgments based on Trading Partner Management (TPM) settings.</span></span> <span data-ttu-id="d27da-104">Les paramètres de l’accusé de réception (ACK) dépendent des informations sur le partenaire.</span><span class="sxs-lookup"><span data-stu-id="d27da-104">The acknowledgment (ACK) settings are dependent on partner information.</span></span> <span data-ttu-id="d27da-105">Type de schéma n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="d27da-105">Schema type is not used.</span></span> <span data-ttu-id="d27da-106">Lorsque [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] reçoit un message d’accusé de réception avec le champ MSH15 contenant AL, SU ou ER, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] peut envoyer un accusé de réception pour ce message en fonction du résultat de l’analyse de l’en-tête de l’accusé de réception et de la configuration du module de plateforme sécurisée.</span><span class="sxs-lookup"><span data-stu-id="d27da-106">When [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] receives an ACK message with the MSH15 field containing AL, SU or ER, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] may send an ACK for this message based on the result of parsing the ACK header and TPM configuration.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="d27da-107">Récupère les paramètres de l’accusé de réception du partenaire et retourne l’une des cinq valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="d27da-107"> retrieves the partner ACK settings and returns one of the following five values:</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d27da-108">La spécification HL7 exige que vous utilisez les éléments 1 à 4 et à remplir le champ MSH15 d’un message d’accusé de réception que vous générez.</span><span class="sxs-lookup"><span data-stu-id="d27da-108">The HL7 specification mandates that you use items 1 through 4 and to populate the MSH15 field of an ACK message that you generate.</span></span> <span data-ttu-id="d27da-109">Est de l’élément 5 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]-spécifique et indique pour ne pas générer un accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="d27da-109">Item 5 is [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]-specific and denotes not to generate an ACK.</span></span>  
  
1.  <span data-ttu-id="d27da-110">AL – toujours</span><span class="sxs-lookup"><span data-stu-id="d27da-110">AL – Always</span></span>  
  
2.  <span data-ttu-id="d27da-111">Nou – jamais</span><span class="sxs-lookup"><span data-stu-id="d27da-111">NE – Never</span></span>  
  
3.  <span data-ttu-id="d27da-112">SU-réussite</span><span class="sxs-lookup"><span data-stu-id="d27da-112">SU – Success</span></span>  
  
4.  <span data-ttu-id="d27da-113">ER : erreur</span><span class="sxs-lookup"><span data-stu-id="d27da-113">ER – Error</span></span>  
  
5.  <span data-ttu-id="d27da-114">NON, ne pas générer un accusé de réception</span><span class="sxs-lookup"><span data-stu-id="d27da-114">NO – Do not generate an ACK</span></span>  
  
## <a name="ack-configuration-inconsistency"></a><span data-ttu-id="d27da-115">Incohérence de configuration de l’accusé de réception</span><span class="sxs-lookup"><span data-stu-id="d27da-115">ACK configuration inconsistency</span></span>  
 <span data-ttu-id="d27da-116">Dans le cas d’incohérence entre les paramètres de l’interface utilisateur configuration l’accusé de réception et les valeurs à l’intérieur de l’instance de message MSH15 et de champs MSH16 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] envoie un accusé de réception lorsqu’une des deux déclencheurs de génération de l’accusé de réception le besoin.</span><span class="sxs-lookup"><span data-stu-id="d27da-116">In the case of inconsistency between the ACK configuration user interface settings and values inside the message instance MSH15 and MSH16 fields, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sends an ACK when one of the two ACK generation triggers require it.</span></span> <span data-ttu-id="d27da-117">Dans le cas d’autres incohérences, les données de l’instance remplace le paramètre dans l’interface utilisateur de configuration.</span><span class="sxs-lookup"><span data-stu-id="d27da-117">In the case of other inconsistencies, the data in the instance will override the setting in the configuration user interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d27da-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d27da-118">See Also</span></span>  
 <span data-ttu-id="d27da-119">[Configuration des accusés de réception de Message](../../adapters-and-accelerators/accelerator-hl7/configuring-message-acknowledgments.md) </span><span class="sxs-lookup"><span data-stu-id="d27da-119">[Configuring Message Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/configuring-message-acknowledgments.md) </span></span>  
 [<span data-ttu-id="d27da-120">Création et le traitement des accusés de réception</span><span class="sxs-lookup"><span data-stu-id="d27da-120">Creating and Processing Acknowledgments</span></span>](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)