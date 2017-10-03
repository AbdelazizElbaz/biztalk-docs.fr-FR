---
title: "L’importation des propriétés de l’accord d’un fichier XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8bf5268-1742-47da-b42f-6472706a9bff
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a3ac08628931ec4111eb1b5a9ad86991344c22d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="importing-agreement-properties-from-an-xml-file"></a><span data-ttu-id="a129d-102">Importation des propriétés d'un accord à partir d'un fichier XML</span><span class="sxs-lookup"><span data-stu-id="a129d-102">Importing Agreement Properties from an XML File</span></span>
<span data-ttu-id="a129d-103">Cette section fournit des instructions sur l'importation des propriétés d'un accord à partir d'un fichier de modèle XML.</span><span class="sxs-lookup"><span data-stu-id="a129d-103">This section provides instructions on how to import agreement properties from an XML template file.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a129d-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="a129d-104">Prerequisites</span></span>  
 <span data-ttu-id="a129d-105">La configuration requise pour exécuter la procédure décrite dans cette rubrique est la suivante :</span><span class="sxs-lookup"><span data-stu-id="a129d-105">The following are prerequisites for performing the procedure in this topic:</span></span>  
  
-   <span data-ttu-id="a129d-106">Vous devez être connecté en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du groupe Opérateurs B2B de  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a129d-106">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
-   <span data-ttu-id="a129d-107">Vous devez avoir exporté un accord dans un fichier de modèle XML, comme décrit dans [propriétés de l’accord exportation vers un fichier XML](../core/exporting-agreement-properties-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="a129d-107">You must have exported an agreement to an XML template file, as described in [Exporting Agreement Properties to an XML FIle](../core/exporting-agreement-properties-to-an-xml-file.md).</span></span>  
  
### <a name="to-import-agreement-properties-from-an-xml-file"></a><span data-ttu-id="a129d-108">Pour importer les propriétés d'un accord à partir d'un fichier XML</span><span class="sxs-lookup"><span data-stu-id="a129d-108">To import agreement properties from an XML file</span></span>  
  
1.  <span data-ttu-id="a129d-109">Dans le [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Console d’Administration, cliquez sur le **Parties** nœud sous la **Administration de BizTalk Server** et **groupe BizTalk** nœuds.</span><span class="sxs-lookup"><span data-stu-id="a129d-109">In the [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Administration Console, click the **Parties** node under the **BizTalk Server Administration** and **BizTalk Group** nodes.</span></span> <span data-ttu-id="a129d-110">Dans le **tiers et profils d’entreprise** page, créez un accord, comme décrit dans [configuration des paramètres généraux (X12)](../core/configuring-general-settings-x12.md).</span><span class="sxs-lookup"><span data-stu-id="a129d-110">In the **Parties and Business Profiles** page, create an agreement as described at [Configuring General Settings (X12)](../core/configuring-general-settings-x12.md).</span></span>  
  
2.  <span data-ttu-id="a129d-111">Dans le **propriétés de l’accord** boîte de dialogue, cliquez sur **charge à partir du modèle**.</span><span class="sxs-lookup"><span data-stu-id="a129d-111">In the **Agreement Properties** dialog box, click **Load From Template**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a129d-112">Le **charge à partir du modèle** bouton est activé uniquement après avoir sélectionné un protocole pour l’accord.</span><span class="sxs-lookup"><span data-stu-id="a129d-112">The **Load From Template** button is enabled only after you select a protocol for the agreement.</span></span> <span data-ttu-id="a129d-113">Lorsque vous spécifiez le protocole, vous déclarez implicitement que vous ne pouvez importer qu'un accord pour le même protocole de codage.</span><span class="sxs-lookup"><span data-stu-id="a129d-113">When you specify the protocol you also implicitly declare that you can only import an agreement for the same encoding protocol.</span></span>  
  
3.  <span data-ttu-id="a129d-114">Dans le **ouvrir** boîte de dialogue, accédez à l’emplacement du fichier XML de modèle, sélectionnez le fichier, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="a129d-114">In the **Open** dialog box, browse to the location of the XML template file, select the file, and then click **Open**.</span></span>  
  
4.  <span data-ttu-id="a129d-115">Dans le **créer un modèle** , cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a129d-115">In the **Create Template** box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a129d-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a129d-116">See Also</span></span>  
 <span data-ttu-id="a129d-117">[Réutilisation des propriétés d’un autre accord](../core/reusing-properties-from-another-agreement.md) </span><span class="sxs-lookup"><span data-stu-id="a129d-117">[Reusing Properties from Another Agreement](../core/reusing-properties-from-another-agreement.md) </span></span>  
 [<span data-ttu-id="a129d-118">Exportation des propriétés de l’accord vers un fichier XML</span><span class="sxs-lookup"><span data-stu-id="a129d-118">Exporting Agreement Properties to an XML FIle</span></span>](../core/exporting-agreement-properties-to-an-xml-file.md)