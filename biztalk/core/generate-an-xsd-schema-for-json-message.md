---
title: "Générer un schéma XSD pour un message JSON | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5453b76c-b282-442f-9eb1-6c2628b38ad5
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b450c74f7d2eda6d3b688c40d0f8e8cde5c66d3b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="generate-an-xsd-schema-for-json-message"></a><span data-ttu-id="7396b-102">Générer un schéma XSD pour un message JSON</span><span class="sxs-lookup"><span data-stu-id="7396b-102">Generate an XSD schema for JSON message</span></span>
> [!NOTE]
>  <span data-ttu-id="7396b-103">Ce didacticiel s'applique uniquement à [!INCLUDE[prague](../includes/prague-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7396b-103">This tutorial applies to [!INCLUDE[prague](../includes/prague-md.md)] only.</span></span>  
  
 <span data-ttu-id="7396b-104">Dans cette solution, une application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit un message JSON.</span><span class="sxs-lookup"><span data-stu-id="7396b-104">In this solution, a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application receives a JSON message.</span></span> <span data-ttu-id="7396b-105">Pour que l'application puisse traiter le message, celui-ci doit être converti en un schéma XSD.</span><span class="sxs-lookup"><span data-stu-id="7396b-105">Before the application can process the message, it must be converted to an XSD schema.</span></span> <span data-ttu-id="7396b-106">Pour cela, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fournit un Assistant Schéma JSON qui créé un schéma XSD à partir d'un message JSON.</span><span class="sxs-lookup"><span data-stu-id="7396b-106">To do so, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides a JSON Schema Wizard that creates an XSD schema from a JSON message.</span></span>  
  
1.  <span data-ttu-id="7396b-107">Dans Visual Studio, créez un nouveau projet [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7396b-107">In Visual Studio, create a new [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="7396b-108">Dans l’Explorateur de solutions, cliquez sur le nom du projet > **ajouter** > **un nouvel élément** > **Assistant schéma JSON**.</span><span class="sxs-lookup"><span data-stu-id="7396b-108">In the Solution Explorer, right-click the project name > **Add** > **New Item** > **JSON Schema Wizard**.</span></span> <span data-ttu-id="7396b-109">Fournissez un nom pour le schéma (`PO.xsd`), puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="7396b-109">Provide a name for the schema (`PO.xsd`), and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="7396b-110">Dans l’Assistant schéma JSON, sur la page d’accueil, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="7396b-110">In the JSON Schema Wizard, on the welcome page, click **Next**.</span></span>  
  
4.  <span data-ttu-id="7396b-111">Dans la page des informations sur le schéma JSON, indiquez l'emplacement du fichier du bon de commande JSON qui est envoyé à l'application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7396b-111">In the JSON Schema Information page, provide the location of the JSON purchase order file that is sent to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application.</span></span> <span data-ttu-id="7396b-112">Entrez un nom de nœud racine, un espace de noms cible, puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="7396b-112">Provide a root node name, a target namespace, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="7396b-113">![Schéma XSD généré pour JSON](../core/media/btsjson-wizard.png "BTSJSON_Wizard")</span><span class="sxs-lookup"><span data-stu-id="7396b-113">![Generated XSD schema for JSON](../core/media/btsjson-wizard.png "BTSJSON_Wizard")</span></span>  
  
5.  <span data-ttu-id="7396b-114">Un schéma avec le nom spécifié est ajouté au projet [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7396b-114">A schema with the specified name is added to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.</span></span> <span data-ttu-id="7396b-115">Le fichier de schéma généré (**PO.xsd**) est également fourni avec l’exemple.</span><span class="sxs-lookup"><span data-stu-id="7396b-115">The generated schema file (**PO.xsd**) is also provided with the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7396b-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7396b-116">See Also</span></span>  
 [<span data-ttu-id="7396b-117">Traitement des messages JSON à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="7396b-117">Processing JSON messages using BizTalk Server</span></span>](../core/processing-json-messages-using-biztalk-server.md)