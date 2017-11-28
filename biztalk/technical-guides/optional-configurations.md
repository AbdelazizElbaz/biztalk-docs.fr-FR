---
title: Configurations facultatives | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f4b0b51-2cad-4cb5-b6cd-4db92bd199fa
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5e938112b5c49b789b76889a45172d5fc0579a1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="optional-configurations"></a><span data-ttu-id="0587f-102">Configurations facultatives</span><span class="sxs-lookup"><span data-stu-id="0587f-102">Optional Configurations</span></span>
<span data-ttu-id="0587f-103">Après avoir importé le Pack d’administration de BizTalk Server, le volet de navigation du volet surveillance affiche les types d’objets qui sont détectés automatiquement.</span><span class="sxs-lookup"><span data-stu-id="0587f-103">After you import the BizTalk Server Management Pack, the navigation pane of the Monitoring pane displays the object types that are discovered automatically.</span></span> <span data-ttu-id="0587f-104">Pour obtenir la liste des types d’objets, consultez [objets du Pack d’administration détecte](../technical-guides/objects-the-management-pack-discovers.md) section.</span><span class="sxs-lookup"><span data-stu-id="0587f-104">For a list of object types, see [Objects the Management Pack Discovers](../technical-guides/objects-the-management-pack-discovers.md) section.</span></span> <span data-ttu-id="0587f-105">Vous pouvez modifier la configuration de la détection par défaut des objets découverts par le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Pack d’administration.</span><span class="sxs-lookup"><span data-stu-id="0587f-105">You can modify the default discovery configuration of objects discovered by the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management Pack.</span></span> <span data-ttu-id="0587f-106">La fonctionnalité de remplacements d’Operations Manager 2007 R2/2012 vous permet de modifier les paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="0587f-106">You use the overrides feature of Operations Manager 2007 R2/2012 to change configuration settings.</span></span>  
  
 <span data-ttu-id="0587f-107">Pour un type d’objet qui n’est pas découvert automatiquement, vous pouvez activer le paramètre de détection automatique dans le **création** volet dans la Console opérateur.</span><span class="sxs-lookup"><span data-stu-id="0587f-107">For an object type that is not automatically discovered, you can enable setting for automatic discovery in the **Authoring** pane in the Operations Console.</span></span>  
  
#### <a name="to-use-an-override-to-change-the-setting-for-automatic-discovery"></a><span data-ttu-id="0587f-108">Pour utiliser un remplacement pour modifier le paramètre de détection automatique</span><span class="sxs-lookup"><span data-stu-id="0587f-108">To use an override to change the setting for automatic discovery</span></span>  
  
1.  <span data-ttu-id="0587f-109">Dans le volet Création, développez **objets du Pack d’administration**, puis cliquez sur **détections**.</span><span class="sxs-lookup"><span data-stu-id="0587f-109">In the Authoring pane, expand **Management Pack Objects**, and then click **Object Discoveries**.</span></span>  
  
2.  <span data-ttu-id="0587f-110">Dans la barre d’outils Operations Manager, cliquez sur **étendue**, filtrez les objets qui apparaissent dans le volet de détails à inclure uniquement les objets BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="0587f-110">On the Operations Manager toolbar, click **Scope**, and filter the objects that appear in the details pane to include only BizTalk Server objects.</span></span>  
  
3.  <span data-ttu-id="0587f-111">Dans le volet de détails, cliquez sur le type d’objet que vous souhaitez modifier le paramétrage.</span><span class="sxs-lookup"><span data-stu-id="0587f-111">In the details pane, click the object type you want to change the setting for.</span></span>  
  
4.  <span data-ttu-id="0587f-112">Dans la barre d’outils Operations Manager, cliquez sur **substitue**, cliquez sur **remplacer la détection d’objets**, puis cliquez sur **pour tous les objets de type :** \<  *nom du type d’objet*>, **pour un groupe, pour un objet spécifique de type :** \< *nom du type d’objet*>, ou **pour tous les objets d’un autre type** .</span><span class="sxs-lookup"><span data-stu-id="0587f-112">On the Operations Manager toolbar, click **Overrides**, click **Override the Object Discovery**, and then click either **For all objects of type:** \<*name of object type*>, **For a group, For a specific object of type:** \<*name of object type*>, or **For all objects of another type**.</span></span>  
  
5.  <span data-ttu-id="0587f-113">Dans le **propriétés du remplacement** boîte de dialogue, cliquez sur le **remplacer** zone pour le **activé** paramètre que vous souhaitez modifier.</span><span class="sxs-lookup"><span data-stu-id="0587f-113">In the **Override Properties** dialog box, click the **Override** box for the **Enabled** parameter you want to change.</span></span>  
  
6.  <span data-ttu-id="0587f-114">Sous **Pack d’administration**, cliquez sur **nouveau** à créer une version non scellée du Pack d’administration, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0587f-114">Under **Management Pack**, click **New** to create an unsealed version of the Management Pack, and then click **OK**.</span></span>  
  
 <span data-ttu-id="0587f-115">Après avoir modifié le paramètre de remplacement, le type d’objet sera automatiquement détecté et apparaîtra dans le volet analyse sous [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0587f-115">After you change the override setting, the object type will be automatically discovered and will appear in the Monitoring pane under [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="0587f-116">Pour plus d’informations sur la définition des remplacements, consultez [remplacements dans Operations Manager 2007 R2/2012](http://go.microsoft.com/fwlink/?LinkId=86870) (http://go.microsoft.com/fwlink/?LinkId=86870).</span><span class="sxs-lookup"><span data-stu-id="0587f-116">For information about setting overrides, see [Overrides in Operations Manager 2007 R2/2012](http://go.microsoft.com/fwlink/?LinkId=86870) (http://go.microsoft.com/fwlink/?LinkId=86870).</span></span>