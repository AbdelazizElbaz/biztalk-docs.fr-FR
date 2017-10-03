---
title: "Schéma Validation2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f9d1576-10df-4c5a-9ae0-618f0dd54b4e
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 317fa8e0e5e557993922bba383ebf5eca460fa69
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="schema-validation"></a><span data-ttu-id="143bc-102">Validation de schéma</span><span class="sxs-lookup"><span data-stu-id="143bc-102">Schema Validation</span></span>
<span data-ttu-id="143bc-103">Le pipeline de réception EDI et le pipeline d'envoi EDI valident un message en utilisant les  schémas suivants :</span><span class="sxs-lookup"><span data-stu-id="143bc-103">The EDI receive pipeline and EDI send pipeline validate a message using the following schemas:</span></span>  
  
-   <span data-ttu-id="143bc-104">**Validation d’enveloppe**: schéma de Service dans `Microsoft.BizTalk.Edi.BaseArtifacts.dll` dans[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]</span><span class="sxs-lookup"><span data-stu-id="143bc-104">**Envelope validation**: Service schema in `Microsoft.BizTalk.Edi.BaseArtifacts.dll` in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]</span></span>  
  
-   <span data-ttu-id="143bc-105">**Validation du document informatisé**: stockent les schémas de Message dans le schéma dans [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI</span><span class="sxs-lookup"><span data-stu-id="143bc-105">**Transaction set validation**: Message schemas in the schema store in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI</span></span>  
  
-   <span data-ttu-id="143bc-106">**Validation de message d’accusé de réception**: CONTRL, 997 et schéma TA1 dans `Microsoft.BizTalk.Edi.BaseArtifacts.dll`.</span><span class="sxs-lookup"><span data-stu-id="143bc-106">**Acknowledgment message validation**: CONTRL, 997, and TA1 schema in `Microsoft.BizTalk.Edi.BaseArtifacts.dll`.</span></span>  
  
 <span data-ttu-id="143bc-107">Les schémas dans `Microsoft.BizTalk.Edi.BaseArtifacts.dll` sont automatiquement déployés par le programme d'installation.</span><span class="sxs-lookup"><span data-stu-id="143bc-107">The schemas in `Microsoft.BizTalk.Edi.BaseArtifacts.dll` are automatically deployed by the setup program.</span></span> <span data-ttu-id="143bc-108">Ces schémas sont répertoriées dans le **schémas** nœud de la **Application EDI BizTalk** dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration.</span><span class="sxs-lookup"><span data-stu-id="143bc-108">These schemas are listed in the **Schemas** node of the **BizTalk EDI Application** in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 <span data-ttu-id="143bc-109">Pour utiliser les schémas de message, installez-les sur le disque dur de votre serveur en  exécutant le fichier à extraction automatique MicrosoftEdiXSDTemplates.exe dans le dossier  [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI, puis déployez-les dans votre projet dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="143bc-109">To use the message schemas, you must install them on the hard drive of your server by executing the MicrosoftEdiXSDTemplates.exe self-extracting file in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI folder, and then deploy them in your project in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
 <span data-ttu-id="143bc-110">**Détermination du schéma**</span><span class="sxs-lookup"><span data-stu-id="143bc-110">**Schema Determination**</span></span>  
  
 <span data-ttu-id="143bc-111">Lorsque le pipeline de réception EDI traite un message de réception, il détermine l'espace de noms du schéma à utiliser en traitant le message via l'accord de partenariat commercial et la  détection de schéma.</span><span class="sxs-lookup"><span data-stu-id="143bc-111">When the EDI receive pipeline processes a receive message, it determines the namespace of the schema to use in processing the message through the agreement lookup and schema discovery process.</span></span> <span data-ttu-id="143bc-112">Pour plus d’informations, consultez [résolution de l’accord, détection de schéma et l’autorisation pour les Messages EDI reçus](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md).</span><span class="sxs-lookup"><span data-stu-id="143bc-112">For more information, see [Agreement Resolution, Schema Discovery, and Authorization for Received EDI Messages](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md).</span></span>  
  
 <span data-ttu-id="143bc-113">Lorsque le pipeline d'envoi EDI crée un message à envoyer, il utilise les propriétés d'accord pour renseigner l'enveloppe, puis exécute la validation du schéma des informations dans les  documents informatisés.</span><span class="sxs-lookup"><span data-stu-id="143bc-113">When the EDI send pipeline creates a message to send, it uses agreement properties to populate the envelope, and then performs schema validation of the information in the transaction set.</span></span> <span data-ttu-id="143bc-114">Après le chargement du schéma, le pipeline d'envoi valide le schéma par rapport aux propriétés de l'accord (ou de l'accord de secours si aucun accord n'a été désigné).</span><span class="sxs-lookup"><span data-stu-id="143bc-114">After loading the schema, the send pipeline validates the schema against agreement properties (or fallback agreement if no agreement has been designated).</span></span> <span data-ttu-id="143bc-115">En cas de validation du schéma, le pipeline valide les documents informatisés par rapport au schéma.</span><span class="sxs-lookup"><span data-stu-id="143bc-115">If the schema validates, the pipeline validates the transaction set against the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="143bc-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="143bc-116">See Also</span></span>  
 [<span data-ttu-id="143bc-117">Validation des messages EDI</span><span class="sxs-lookup"><span data-stu-id="143bc-117">EDI Message Validation</span></span>](../core/edi-message-validation.md)