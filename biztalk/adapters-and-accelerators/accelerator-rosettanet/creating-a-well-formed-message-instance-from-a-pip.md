---
title: "Création d’une Instance de Message bien formée à partir d’une adresse PIP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message templates
- PIPs, message templates
ms.assetid: fed3698c-25d9-40ca-878a-60171f425bec
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e16020afb17d17c8add8e973ade0cd0c5cfcbbc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-well-formed-message-instance-from-a-pip"></a><span data-ttu-id="63d5f-102">Création d'une instance de message bien formée à partir d'un processus PIP</span><span class="sxs-lookup"><span data-stu-id="63d5f-102">Creating a Well-Formed Message Instance from a PIP</span></span>
<span data-ttu-id="63d5f-103">Cette rubrique explique comment produire une instance de message bien formée.</span><span class="sxs-lookup"><span data-stu-id="63d5f-103">This topic describes how to produce a well-formed message instance.</span></span> <span data-ttu-id="63d5f-104">Vous pouvez générer un modèle pour une instance de message à partir du processus d'interface entres partenaires (PIP).</span><span class="sxs-lookup"><span data-stu-id="63d5f-104">You can generate a template for a message instance from the Partner Interface Process (PIP).</span></span> <span data-ttu-id="63d5f-105">Après avoir effectué cette opération, vous devez modifier ce modèle, afin qu'il soit bien formé, avant d'ajouter vos données.</span><span class="sxs-lookup"><span data-stu-id="63d5f-105">After doing this, you have to modify that template, so that it is well formed, before adding your data.</span></span>  
  
### <a name="to-generate-a-message-instance-template-from-the-pip"></a><span data-ttu-id="63d5f-106">Pour générer un modèle d'instance de message à partir du PIP</span><span class="sxs-lookup"><span data-stu-id="63d5f-106">To generate a message instance template from the PIP</span></span>  
  
1.  <span data-ttu-id="63d5f-107">Démarrez **Microsoft Visual Studio 2012**.</span><span class="sxs-lookup"><span data-stu-id="63d5f-107">Start **Microsoft Visual Studio 2012**.</span></span>  
  
2.  <span data-ttu-id="63d5f-108">Dans le menu **Fichier** , pointez sur **Ouvrir**, puis cliquez sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="63d5f-108">On the **File** menu, point to **Open**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="63d5f-109">Recherchez \< *lecteur*> \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNetSDK\Schemas, cliquez sur **RNPIPs.btproj**, puis cliquez sur **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="63d5f-109">Locate \<*drive*>\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNetSDK\Schemas, click **RNPIPs.btproj**, and then click **Open**.</span></span>  
  
4.  <span data-ttu-id="63d5f-110">Dans l'Explorateur de solutions, développez **RNPIPs**, puis cliquez avec le bouton droit sur le PIP pour lequel vous voulez créer une instance.</span><span class="sxs-lookup"><span data-stu-id="63d5f-110">In Solution Explorer, expand **RNPIPs**, and then right-click the PIP for which you want to create an instance.</span></span>  
  
5.  <span data-ttu-id="63d5f-111">Cliquez sur **Générer l'instance**.</span><span class="sxs-lookup"><span data-stu-id="63d5f-111">Click **Generate Instance**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="63d5f-112">Cela génère un fichier qui porte le nom du PIP, avec « _output » ajouté au nom de fichier et dont l'extension est .xml.</span><span class="sxs-lookup"><span data-stu-id="63d5f-112">This generates a file named after the PIP, with "_output" appended to the file name, and with an .xml extension.</span></span> <span data-ttu-id="63d5f-113">Indique l’endroit où une instruction dans le volet de sortie [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] a généré l’instance.</span><span class="sxs-lookup"><span data-stu-id="63d5f-113">A statement in the Output pane indicates where [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] generated the instance.</span></span>  
  
### <a name="to-modify-the-message-instance-template"></a><span data-ttu-id="63d5f-114">Pour modifier le modèle d'instance de message</span><span class="sxs-lookup"><span data-stu-id="63d5f-114">To modify the message instance template</span></span>  
  
1.  <span data-ttu-id="63d5f-115">Dans [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorateur de solutions, recherchez le dossier contenant le fichier XML, double-cliquez sur le nom de fichier pour ouvrir le dossier.</span><span class="sxs-lookup"><span data-stu-id="63d5f-115">In [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, locate the folder holding the XML file, and double-click the file name to open the folder.</span></span>  
  
2.  <span data-ttu-id="63d5f-116">Ajoutez, avant tout le reste du texte, une balise d'en-tête XML indiquant la version du code XML et le codage.</span><span class="sxs-lookup"><span data-stu-id="63d5f-116">Add an XML header tag before all other text indicating the version of XML and the encoding.</span></span> <span data-ttu-id="63d5f-117">Exemple :</span><span class="sxs-lookup"><span data-stu-id="63d5f-117">For example:</span></span>  
  
    ```  
    <?xml version="1.0" encoding="UTF-8" ?>  
    ```  
  
3.  <span data-ttu-id="63d5f-118">Après la ligne que vous venez d'ajouter, ajoutez une ligne DOCTYPE indiquant le DTD.</span><span class="sxs-lookup"><span data-stu-id="63d5f-118">After the line that you just added, add a DOCTYPE line indicating the DTD.</span></span> <span data-ttu-id="63d5f-119">Par exemple, pour une instance de demande de bon de commande 3A4, la ligne serait la suivante :</span><span class="sxs-lookup"><span data-stu-id="63d5f-119">For example, for a 3A4 Purchase Order Request instance, the line would be as follows:</span></span>  
  
    ```  
    <!DOCTYPE Pip3A4PurchaseOrderRequest SYSTEM "3A4_MS_V02_02_PurchaseOrderRequest.dtd">  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="63d5f-120">Chaque instance de message doit inclure la ligne DOCTYPE à traiter.</span><span class="sxs-lookup"><span data-stu-id="63d5f-120">Each message instance must include the DOCTYPE line to be processed.</span></span>  
  
4.  <span data-ttu-id="63d5f-121">Vous pouvez maintenant personnaliser cette instance de message pour répondre aux besoins de votre entreprise.</span><span class="sxs-lookup"><span data-stu-id="63d5f-121">You may now customize this message instance to suit your business needs.</span></span> <span data-ttu-id="63d5f-122">Modifiez l'instance XML afin qu'elle n'utilise pas des préfixes d'espace de noms ou des espaces de noms XML.</span><span class="sxs-lookup"><span data-stu-id="63d5f-122">Modify the XML instance so that it does not use XML namespaces or namespace prefixes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63d5f-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63d5f-123">See Also</span></span>  
 [<span data-ttu-id="63d5f-124">Guide de programmation</span><span class="sxs-lookup"><span data-stu-id="63d5f-124">Programming Guide</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)