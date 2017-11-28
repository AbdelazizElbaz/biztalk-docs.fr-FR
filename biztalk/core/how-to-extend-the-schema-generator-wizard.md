---
title: "Comment étendre l’Assistant génération de schéma | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- utilities, Schema Generator Wizard
- Schema Generator Wizard
ms.assetid: ea4b5532-f904-4da0-9612-e092e7e4edc1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 11db44e07191b0996043dd6b819ef2ba9162a0e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-extend-the-schema-generator-wizard"></a><span data-ttu-id="27cbe-102">Comment étendre l’Assistant génération de schéma</span><span class="sxs-lookup"><span data-stu-id="27cbe-102">How to Extend the Schema Generator Wizard</span></span>
<span data-ttu-id="27cbe-103">Comment étendre l’Assistant génération de schémas et comment créer un nouvel Assistant de génération de schéma.</span><span class="sxs-lookup"><span data-stu-id="27cbe-103">How to extend the existing Schema Generator Wizard and how to create a new wizard for schema generation.</span></span>  
  
## <a name="extend-the-existing-schema-wizard"></a><span data-ttu-id="27cbe-104">Étendre l’Assistant schéma existant</span><span class="sxs-lookup"><span data-stu-id="27cbe-104">Extend the existing schema wizard</span></span>  
  
1.  <span data-ttu-id="27cbe-105">Implémentez l’interface ISchemaGenerator pour créer un nouveau module de génération de schéma que vous pouvez intégrer à l’Assistant génération de schémas.</span><span class="sxs-lookup"><span data-stu-id="27cbe-105">Implement the ISchemaGenerator interface to create a new schema generator module that you can integrate into the existing Schema Generator Wizard.</span></span>  
  
    ```  
    public interface ISchemaGenerator  
    {  
    //Method to extract a schema from a document.  
    void GenerateSchema(string inputDocument,string outputDocumentPath);  
  
    //Method to extract the errors.  
    [return : MarshalAs(UnmanagedType.SafeArray, SafeArraySubType = VarEnum.VT_VARIANT )]object [] Errors();  
  
    //Method to extract the warnings.  
    [return : MarshalAs(UnmanagedType.SafeArray, SafeArraySubType = VarEnum.VT_VARIANT )]object [] Warnings();  
  
    //Method to extract the referenced schemas.  
    [return : MarshalAs(UnmanagedType.SafeArray, SafeArraySubType = VarEnum.VT_VARIANT )]object [] ReferencedSchemas();  
    }  
    ```  
  
2.  <span data-ttu-id="27cbe-106">Déposez l'assembly généré dans le dossier d'installation Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] suivant :</span><span class="sxs-lookup"><span data-stu-id="27cbe-106">Drop the resulting assembly in the following Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation folder:</span></span>  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="27cbe-107">Extensions de l’éditeur \Developer Tools\Schema</span><span class="sxs-lookup"><span data-stu-id="27cbe-107">\Developer Tools\Schema Editor Extensions</span></span>  
  
     <span data-ttu-id="27cbe-108">La prochaine fois que vous exécuterez l'Assistant Génération de schémas, il utilisera automatiquement le nouveau module de génération de schémas.</span><span class="sxs-lookup"><span data-stu-id="27cbe-108">The next time you run the Schema Generator Wizard, it will automatically pick up your new schema generator module.</span></span>  
  
 <span data-ttu-id="27cbe-109">Effectuez la procédure ci-dessous pour créer un Assistant Schéma.</span><span class="sxs-lookup"><span data-stu-id="27cbe-109">Use the following procedure to create a new schema wizard.</span></span>  
  
 <span data-ttu-id="27cbe-110">**Emplacement dans le Kit de développement logiciel**</span><span class="sxs-lookup"><span data-stu-id="27cbe-110">**Location in SDK**</span></span>  
  
 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="27cbe-111">Générateur de \SDK\Utilities\Schema</span><span class="sxs-lookup"><span data-stu-id="27cbe-111">\SDK\Utilities\Schema Generator</span></span>  
  
### <a name="create-a-new-schema-wizard"></a><span data-ttu-id="27cbe-112">Assistant Création d’un nouveau schéma</span><span class="sxs-lookup"><span data-stu-id="27cbe-112">Create a new schema wizard</span></span>  
  
1.  <span data-ttu-id="27cbe-113">Exécutez InstallDTD.vbs pour installer le fichier Microsoft.BizTalk.DTDToXSDGenerator.dll dans [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Developer Tools\Schema Extensions de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="27cbe-113">Run InstallDTD.vbs to install Microsoft.BizTalk.DTDToXSDGenerator.dll to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Developer Tools\Schema Editor Extensions.</span></span> <span data-ttu-id="27cbe-114">DTDToXSDGenerator.dll présente les classes que vous pouvez utiliser pour convertir des fichiers DTD en fichiers XSD.</span><span class="sxs-lookup"><span data-stu-id="27cbe-114">DTDToXSDGenerator.dll exposes classes you can use to convert DTD files to XSD.</span></span>  
  
2.  <span data-ttu-id="27cbe-115">Exécutez InstallWFX.vbs pour installer le fichier Microsoft.BizTalk.WFXToXSDGenerator.dll dans [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Developer Tools\Schema Extensions de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="27cbe-115">Run InstallWFX.vbs to install Microsoft.BizTalk.WFXToXSDGenerator.dll to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Developer Tools\Schema Editor Extensions.</span></span> <span data-ttu-id="27cbe-116">WFXToXSDGenerator.dll présente les classes que vous pouvez utiliser pour convertir les fichiers WFX en fichiers XSD.</span><span class="sxs-lookup"><span data-stu-id="27cbe-116">WFXToXSDGenerator.dll exposes classes you can use to convert WFX files to XSD.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27cbe-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27cbe-117">See Also</span></span>  
 [<span data-ttu-id="27cbe-118">Utilitaires dans le Kit de développement</span><span class="sxs-lookup"><span data-stu-id="27cbe-118">Utilities in the SDK</span></span>](../core/utilities-in-the-sdk.md)