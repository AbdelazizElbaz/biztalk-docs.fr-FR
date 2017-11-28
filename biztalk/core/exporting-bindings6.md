---
title: Exportation Bindings6 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- bindings, exporting
- exporting, bindings
ms.assetid: 052a429e-3237-44d4-8933-00aa5edfb212
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3362984eca1dcec4fb68bfbac92c30da81de8a3b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="exporting-bindings"></a><span data-ttu-id="cac34-102">L’exportation des liaisons</span><span class="sxs-lookup"><span data-stu-id="cac34-102">Exporting Bindings</span></span>
<span data-ttu-id="cac34-103">Les sections de cette rubrique décrivent comment exporter des liaisons d'un groupe, d'un assembly ou d'une application BizTalk dans un fichier .xml.</span><span class="sxs-lookup"><span data-stu-id="cac34-103">The topics in this section describe how to export bindings for a BizTalk group, assembly, or application into an .xml file.</span></span> <span data-ttu-id="cac34-104">Les liaisons déterminent la façon dont les hôtes, ports d'envoi, groupes de ports d'envoi, ports de réception, emplacements de réception et parties sont associés aux orchestrations, pipelines, mappages et schémas. Vous pouvez ensuite importer les liaisons à partir du fichier .xml dans un autre groupe ou une autre application.</span><span class="sxs-lookup"><span data-stu-id="cac34-104">(Bindings define how hosts, send ports, send port groups, receive ports, receive locations, parties are associated with orchestrations, pipelines, maps, and schemas.) You can then import the bindings from the .xml file into another group or application.</span></span> <span data-ttu-id="cac34-105">Les liaisons que vous importez remplacent les liaisons existantes portant le même nom dans le groupe ou l'application.</span><span class="sxs-lookup"><span data-stu-id="cac34-105">Importing bindings overwrites any existing bindings of the same name in the group or application.</span></span> <span data-ttu-id="cac34-106">Vous pouvez aussi ajouter des liaisons à une application, ce qui n'écrase pas les liaisons existantes.</span><span class="sxs-lookup"><span data-stu-id="cac34-106">You can also add bindings to an application, which does not overwrite existing bindings.</span></span> <span data-ttu-id="cac34-107">Les liaisons ajoutées ne prennent effet qu'une fois l'application importée.</span><span class="sxs-lookup"><span data-stu-id="cac34-107">The bindings that you add do not take effect until you import the application.</span></span>  
  
 <span data-ttu-id="cac34-108">Les fichiers de liaison peuvent accélérer le déploiement de l'application dans les cas suivants en évitant le recours à la configuration manuelle :</span><span class="sxs-lookup"><span data-stu-id="cac34-108">You may find that using binding files speeds application deployment in the following scenarios by avoiding the need to manually configure bindings:</span></span>  
  
-   <span data-ttu-id="cac34-109">Déplacement d'une application d'un environnement de déploiement à un autre</span><span class="sxs-lookup"><span data-stu-id="cac34-109">Moving an application from one deployment environment to another.</span></span>  
  
-   <span data-ttu-id="cac34-110">Mise à jour d'un assembly</span><span class="sxs-lookup"><span data-stu-id="cac34-110">Updating an assembly.</span></span>  
  
-   <span data-ttu-id="cac34-111">Déploiement d'un assembly avec ses liaisons dans plusieurs groupes BizTalk</span><span class="sxs-lookup"><span data-stu-id="cac34-111">Deploying an assembly together with its bindings to multiple BizTalk groups.</span></span>  
  
 <span data-ttu-id="cac34-112">Pour plus d’informations sur l’utilisation des fichiers de liaison à ces fins, consultez [déploiement d’applications et des fichiers de liaison](../core/binding-files-and-application-deployment.md).</span><span class="sxs-lookup"><span data-stu-id="cac34-112">For more information about using binding files for these purposes, see [Binding Files and Application Deployment](../core/binding-files-and-application-deployment.md).</span></span>  
  
 <span data-ttu-id="cac34-113">Pour plus d’informations sur l’importation et l’ajout de liaisons, consultez [comment importer les liaisons dans un groupe BizTalk](../core/how-to-import-bindings-into-a-biztalk-group.md), [comment importer les liaisons dans une Application BizTalk](../core/how-to-import-bindings-into-a-biztalk-application.md), et [l’ajout d’une liaison Fichier à une Application](../core/how-to-add-a-binding-file-to-an-application2.md).</span><span class="sxs-lookup"><span data-stu-id="cac34-113">For more information about importing and adding bindings, see [How to Import Bindings into a BizTalk Group](../core/how-to-import-bindings-into-a-biztalk-group.md), [How to Import Bindings into a BizTalk Application](../core/how-to-import-bindings-into-a-biztalk-application.md), and [How to Add a Binding File to an Application](../core/how-to-add-a-binding-file-to-an-application2.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cac34-114">Le fichier de liaison peut contenir des données sensibles.</span><span class="sxs-lookup"><span data-stu-id="cac34-114">The binding file may contain sensitive data.</span></span> <span data-ttu-id="cac34-115">Veillez à sécuriser le fichier.</span><span class="sxs-lookup"><span data-stu-id="cac34-115">Be sure to take steps to secure the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cac34-116">Pour des raisons de sécurité, lorsque vous exportez un fichier de liaison, BizTalk Server ne conserve pas les mots de passe des liaisons du fichier.</span><span class="sxs-lookup"><span data-stu-id="cac34-116">For security reasons, when you export a binding file, BizTalk Server removes the passwords for the bindings from the file.</span></span> <span data-ttu-id="cac34-117">Une fois les liaisons importées, vous devez reconfigurer les mots de passe des ports d'envoi et des emplacements de réception pour qu'ils fonctionnent.</span><span class="sxs-lookup"><span data-stu-id="cac34-117">After importing the bindings, you must reconfigure passwords for send ports and receive locations before they will function.</span></span> <span data-ttu-id="cac34-118">Vous configurez ces mots de passe dans la boîte de dialogue Propriétés du transport de la console Administration de BizTalk Server pour le port d'envoi ou l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="cac34-118">You configure passwords in the Transport Properties dialog box of the BizTalk Server Administration console for the send port or receive location.</span></span> <span data-ttu-id="cac34-119">Pour obtenir des instructions, consultez [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md).</span><span class="sxs-lookup"><span data-stu-id="cac34-119">For instructions, see [How to Create a Send Port](../core/how-to-create-a-send-port2.md).</span></span> <span data-ttu-id="cac34-120">Voir aussi [la création d’un emplacement de réception](../core/how-to-create-a-receive-location.md).</span><span class="sxs-lookup"><span data-stu-id="cac34-120">See also [How to Create a Receive Location](../core/how-to-create-a-receive-location.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cac34-121">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="cac34-121">In This Section</span></span>  
  
-   [<span data-ttu-id="cac34-122">Comment exporter des liaisons d’un groupe BizTalk</span><span class="sxs-lookup"><span data-stu-id="cac34-122">How to Export Bindings for a BizTalk Group</span></span>](../core/how-to-export-bindings-for-a-biztalk-group.md)  
  
-   [<span data-ttu-id="cac34-123">Comment exporter des liaisons pour une Application BizTalk</span><span class="sxs-lookup"><span data-stu-id="cac34-123">How to Export Bindings for a BizTalk Application</span></span>](../core/how-to-export-bindings-for-a-biztalk-application.md)  
  
-   [<span data-ttu-id="cac34-124">Comment exporter des liaisons d’un Assembly BizTalk</span><span class="sxs-lookup"><span data-stu-id="cac34-124">How to Export Bindings for a BizTalk Assembly</span></span>](../core/how-to-export-bindings-for-a-biztalk-assembly.md)  
  
-   [<span data-ttu-id="cac34-125">Comment exporter des liaisons pour une Solution EDI AS2</span><span class="sxs-lookup"><span data-stu-id="cac34-125">How to Export Bindings for an EDI-AS2 Solution</span></span>](../core/how-to-export-bindings-for-an-edi-as2-solution.md)