---
title: "Validation d’un schéma (EDI) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6175460-2dcf-4fef-b770-02f0a058bf93
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44cd2672f7ba9be796c1ff802be51324fbfe3256
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="validating-a-schema-edi"></a><span data-ttu-id="9386b-102">Validation d'un schéma (EDI)</span><span class="sxs-lookup"><span data-stu-id="9386b-102">Validating a Schema (EDI)</span></span>
<span data-ttu-id="9386b-103">Vous pouvez valider un schéma EDI pendant la phase de conception.</span><span class="sxs-lookup"><span data-stu-id="9386b-103">You can validate an EDI schema at design time.</span></span> <span data-ttu-id="9386b-104">Pour ce faire, utilisez les extensions de l'outil XML à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans l'environnement [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9386b-104">To do so, you use the XML Tool extensions to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] environment.</span></span> <span data-ttu-id="9386b-105">L'opération de validation du schéma consiste à valider un schéma selon des règles EDI.</span><span class="sxs-lookup"><span data-stu-id="9386b-105">The validate-schema operation validates the schema based on EDI rules.</span></span> <span data-ttu-id="9386b-106">Il est inutile de désigner une instance de message entrant pour valider un schéma.</span><span class="sxs-lookup"><span data-stu-id="9386b-106">You do not have to designate an input message instance to validate a schema.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9386b-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="9386b-107">Prerequisites</span></span>  
 <span data-ttu-id="9386b-108">Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9386b-108">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-validate-a-schema"></a><span data-ttu-id="9386b-109">Pour valider un schéma</span><span class="sxs-lookup"><span data-stu-id="9386b-109">To validate a schema</span></span>  
  
1.  <span data-ttu-id="9386b-110">Ouvrez un projet dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9386b-110">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open a project.</span></span> <span data-ttu-id="9386b-111">Dans l'Explorateur de solutions, ajoutez au projet le schéma du message que vous souhaitez valider.</span><span class="sxs-lookup"><span data-stu-id="9386b-111">To the project in Solution Explorer, add the message schema that you want to validate.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9386b-112">Ces derniers se trouvent dans le sous-dossier approprié, sous le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI.</span><span class="sxs-lookup"><span data-stu-id="9386b-112">The message schemas are located in the appropriate subfolder under the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI folder.</span></span> <span data-ttu-id="9386b-113">Pour plus d’informations sur l’installation des fichiers de schéma, consultez [comment installer les fichiers de schéma EDI](http://msdn.microsoft.com/library/787f45d9-d95d-40f4-a4ac-0a0e711f7550).</span><span class="sxs-lookup"><span data-stu-id="9386b-113">For information on installing the schema files, see [How to Install EDI Schema Files](http://msdn.microsoft.com/library/787f45d9-d95d-40f4-a4ac-0a0e711f7550).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9386b-114">Il est inutile de générer un projet pour valider un schéma.</span><span class="sxs-lookup"><span data-stu-id="9386b-114">You do not have to build the project to validate a schema.</span></span>  
  
2.  <span data-ttu-id="9386b-115">Cliquez sur le schéma dans l’Explorateur de solutions, puis cliquez sur **valider le schéma**.</span><span class="sxs-lookup"><span data-stu-id="9386b-115">Right-click the schema in Solution Explorer, and then click **Validate Schema**.</span></span>  
  
3.  <span data-ttu-id="9386b-116">Vérifiez qu'il y a un message dans la fenêtre Sortie indiquant que l'opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="9386b-116">Verify that there is a message in the Output window indicating that the operation succeeded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9386b-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9386b-117">See Also</span></span>  
 [<span data-ttu-id="9386b-118">À l’aide d’outils au moment du Design XML</span><span class="sxs-lookup"><span data-stu-id="9386b-118">Using Design-Time XML Tools</span></span>](../core/using-design-time-xml-tools.md)