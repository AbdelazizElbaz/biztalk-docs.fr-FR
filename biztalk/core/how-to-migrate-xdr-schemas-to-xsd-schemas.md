---
title: "Comment migrer les schémas XDR vers des schémas XSD | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90bde0d0-bfe6-4d6c-823c-8ed9c0e15783
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7fb0709ca0bd8b67e1549ba740c5810138f61739
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-migrate-xdr-schemas-to-xsd-schemas"></a><span data-ttu-id="47e97-102">Migration des schémas XDR vers des schémas XSD</span><span class="sxs-lookup"><span data-stu-id="47e97-102">How to Migrate XDR Schemas to XSD Schemas</span></span>
<span data-ttu-id="47e97-103">Si vous migrez des schémas à partir d'une version précédente de BizTalk Server, vous devrez convertir vos schémas XDR (XML-Data Reduced) en des schémas de langage XSD (XML Schema Definition).</span><span class="sxs-lookup"><span data-stu-id="47e97-103">If you are migrating schemas from a previous version of BizTalk Server, you will need to convert your XML-Data Reduced (XDR) schemas into XML Schema definition (XSD) language schemas.</span></span> <span data-ttu-id="47e97-104">Cette rubrique décrit les étapes nécessaires à cette migration.</span><span class="sxs-lookup"><span data-stu-id="47e97-104">This topic describes the necessary steps.</span></span>  
  
### <a name="to-generate-an-xsd-schema-from-an-xdr-schema"></a><span data-ttu-id="47e97-105">Pour générer un schéma XSD à partir d'un schéma XDR</span><span class="sxs-lookup"><span data-stu-id="47e97-105">To generate an XSD schema from an XDR schema</span></span>  
  
1.  <span data-ttu-id="47e97-106">Dans **l’Explorateur de solutions**, cliquez sur le projet BizTalk approprié, pointez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.</span><span class="sxs-lookup"><span data-stu-id="47e97-106">In **Solution Explorer**, right-click the relevant BizTalk project, point to **Add**, and then click **Add Generated Items**.</span></span>  
  
2.  <span data-ttu-id="47e97-107">Dans le  **ajouter les éléments générés - \<* BizTalk ProjectName*> ** boîte de dialogue le **modèles** , cliquez sur **générer les schémas**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="47e97-107">In the **Add Generated Item - \<*BizTalk ProjectName*>** dialog box, in the **Templates** section, click **Generate Schemas**, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="47e97-108">Dans le **générer les schémas** boîte de dialogue le **type de Document** liste, sélectionnez **schéma XDR**.</span><span class="sxs-lookup"><span data-stu-id="47e97-108">In the **Generate Schemas** dialog box, in the **Document type** list, select **XDR Schema**.</span></span>  
  
4.  <span data-ttu-id="47e97-109">Cliquez sur **Parcourir**, recherchez le fichier de schéma XDR que vous souhaitez migrer, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="47e97-109">Click **Browse**, locate the XDR schema file you want to migrate, and then click **OK**.</span></span>  
  
     <span data-ttu-id="47e97-110">Un nouveau schéma est généré à partir du fichier de schéma XDR spécifié. Il porte le même nom que ce fichier ainsi que l'extension .xsd et est ensuite ouvert dans l'Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="47e97-110">A new schema is generated from the specified XDR schema file, using the same name as that file with the .xsd extension, and then opened in BizTalk Editor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="47e97-111">Évitez d'utiliser les mots réservés C# et les noms de type et d'espace de noms .NET Framework (tels que Système) en tant que noms de nœud racine de schéma ou que noms de fichier.</span><span class="sxs-lookup"><span data-stu-id="47e97-111">Avoid using C# reserved words and .NET Framework type and namespace names (such as System) as schema root node names or as file names.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47e97-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47e97-112">See Also</span></span>  
 <span data-ttu-id="47e97-113">[Gestion des schémas dans des projets](../core/managing-schemas-within-projects.md) </span><span class="sxs-lookup"><span data-stu-id="47e97-113">[Managing Schemas Within Projects](../core/managing-schemas-within-projects.md) </span></span>  
 [<span data-ttu-id="47e97-114">Migration des enregistrements de fichier plat</span><span class="sxs-lookup"><span data-stu-id="47e97-114">Migrating Flat File Records</span></span>](../core/migrating-flat-file-records.md)