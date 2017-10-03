---
title: "Mise à jour les liaisons dans une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe4ee4d8-67bf-4137-94e2-8274107c8ed6
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2d4d30296a2bb81b3685793884010f02eb950828
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="updating-the-bindings-in-an-application"></a><span data-ttu-id="d893a-102">Mise à jour les liaisons de l’Application</span><span class="sxs-lookup"><span data-stu-id="d893a-102">Updating the Bindings in an Application</span></span>
<span data-ttu-id="d893a-103">Lorsque vous mettez à jour un assembly dans une application, ses liaisons sont généralement remplacées, faute de quoi l'assembly risque de ne pas être lié, vous obligeant à une reconfiguration manuelle des liaisons.</span><span class="sxs-lookup"><span data-stu-id="d893a-103">When you update an assembly in an application, its bindings are often overwritten or else the assembly may not be bound at all, forcing you to manually reconfigure bindings.</span></span> <span data-ttu-id="d893a-104">Pour éviter ce problème, vous pouvez utiliser un fichier de liaison à mettre à jour de la même version de l’assembly ou de mettre à jour un assembly avec une version plus récente.</span><span class="sxs-lookup"><span data-stu-id="d893a-104">To avoid this, you can use a binding file to update the same version of the assembly or update an assembly with a newer version.</span></span>  
  
## <a name="updating-the-same-version-of-an-assembly"></a><span data-ttu-id="d893a-105">Mise à jour de la même Version d’un Assembly</span><span class="sxs-lookup"><span data-stu-id="d893a-105">Updating the Same Version of an Assembly</span></span>  
 <span data-ttu-id="d893a-106">si l'assembly possède des ports dynamiques ou des ports à liaison anticipée et que vous ayez modifié leur configuration dans la console Administration de BizTalk Server, vous perdez ces paramètres lors de la mise à jour de l'assembly avec un assembly de même version.</span><span class="sxs-lookup"><span data-stu-id="d893a-106">If the assembly has early bound ports or dynamic ports, and you changed the port configuration in the BizTalk Server Administration console, the settings will be lost when you update the assembly with an assembly having the same version number.</span></span> <span data-ttu-id="d893a-107">Vous pouvez exporter un fichier de liaison pour l’assembly que vous vous apprêtez à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="d893a-107">You can export a binding file for the assembly that you are going to update.</span></span> <span data-ttu-id="d893a-108">Après la mise à jour de l’assembly, vous pouvez importer l’assembly dans l’application et puis importer son fichier de liaison pour réappliquer les liaisons précédentes.</span><span class="sxs-lookup"><span data-stu-id="d893a-108">After updating the assembly, you can import the assembly into the application and then import its binding file to reapply the previous bindings.</span></span>  
  
## <a name="updating-an-assembly-with-a-newer-version"></a><span data-ttu-id="d893a-109">Mise à jour d’un Assembly avec une Version plus récente</span><span class="sxs-lookup"><span data-stu-id="d893a-109">Updating an Assembly with a Newer Version</span></span>  
 <span data-ttu-id="d893a-110">Vous pouvez mettre à jour la version d’un assembly en exportant la liaison associée à un assembly unique dans un fichier de liaison, modification du fichier de liaison afin de refléter une nouvelle version de l’assembly, puis importer les liaisons de l’assembly dans l’application.</span><span class="sxs-lookup"><span data-stu-id="d893a-110">You can update the version of an assembly by exporting the binding associated with a single assembly into a binding file, editing the binding file to reflect a new assembly version, and then importing the bindings of the assembly into the application.</span></span> <span data-ttu-id="d893a-111">Pour plus d’informations sur la modification d’un fichier de liaison, consultez [personnalisation des fichiers de liaison](http://go.microsoft.com/fwlink/?LinkID=155000) (lien hypertexte « http://go.microsoft.com/fwlink/?LinkID=155000 » http://go.microsoft.com/fwlink/?LinkID=155000) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="d893a-111">For more information about editing a binding file, see [Customizing Binding Files](http://go.microsoft.com/fwlink/?LinkID=155000) ( HYPERLINK "http://go.microsoft.com/fwlink/?LinkID=155000" http://go.microsoft.com/fwlink/?LinkID=155000) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>