---
title: "Concepteur de Configuration d’adaptateur personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9b231c3-3948-4db8-b4f0-d9c21c31b168
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e876892b3eef9e5dd47c51c64997d84a0f0dc98
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="custom-adapter-configuration-designer"></a><span data-ttu-id="d8f66-102">Concepteur de Configuration d’adaptateur personnalisé</span><span class="sxs-lookup"><span data-stu-id="d8f66-102">Custom Adapter Configuration Designer</span></span>
<span data-ttu-id="d8f66-103">Les concepteurs personnalisés doivent être créés dans une bibliothèque de classes .NET.</span><span class="sxs-lookup"><span data-stu-id="d8f66-103">You need to build the custom designers into a .NET class library.</span></span> <span data-ttu-id="d8f66-104">Vous pouvez les incorporer dans la DLL de l'adaptateur ou créer une DLL distincte.</span><span class="sxs-lookup"><span data-stu-id="d8f66-104">You may incorporate them into the DLL for the adapter or build a separate DLL.</span></span> <span data-ttu-id="d8f66-105">Une fois que vous avez créé un assembly de concepteur, vous devez le référencer par le biais de décorations, tout comme une description ou une catégorie.</span><span class="sxs-lookup"><span data-stu-id="d8f66-105">After you build a designer assembly, you must reference it through decorations, just like a description or a category.</span></span> <span data-ttu-id="d8f66-106">La référence inclut une spécification de l'assembly et un nom de classe complet.</span><span class="sxs-lookup"><span data-stu-id="d8f66-106">The reference includes a specification of the assembly and a fully qualified class name to use.</span></span>  
  
 <span data-ttu-id="d8f66-107">Ces décorations prend en charge deux moyens pour référencer le concepteur personnalisé : sous la forme d’un assembly global dans le global assembly cache ou un assembly externe situé sur le disque.</span><span class="sxs-lookup"><span data-stu-id="d8f66-107">These decorations support two ways of referencing the specific custom designer: as a global assembly in the global assembly cache or as an external assembly located on the disk.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d8f66-108">Il existe deux chemins d’accès possibles au moment du design assembly : vous pouvez spécifier le chemin d’accès absolu pour les éditeurs de type et les convertisseurs utilisés dans la configuration XSD dans le XSD lui-même (le chemin d’accès relatif n’est pas prise en charge), ou vous pouvez stocker les convertisseurs et éditeurs de type dans la liste globale cache d’assembly et de ne pas avoir un chemin d’accès absolu.</span><span class="sxs-lookup"><span data-stu-id="d8f66-108">There are two possible design-time assembly paths: You can specify the absolute path to the type editors and converters used in the configuration XSD in the XSD itself (relative path is not supported), or you can store the type editors and converters in the global assembly cache and not need an absolute path.</span></span>  
  
## <a name="global-assembly-cache-designer-use"></a><span data-ttu-id="d8f66-109">Utilisation du concepteur du Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="d8f66-109">Global Assembly Cache Designer Use</span></span>  
 <span data-ttu-id="d8f66-110">Le Global Assembly Cache stocke les assemblys en fonction de leur nom, clé publique, version et culture.</span><span class="sxs-lookup"><span data-stu-id="d8f66-110">The global assembly cache stores assemblies by assembly name, public key, version, and culture.</span></span> <span data-ttu-id="d8f66-111">Il est donc recommandé de :</span><span class="sxs-lookup"><span data-stu-id="d8f66-111">Because of this, it is recommended that you:</span></span>  
  
1.  <span data-ttu-id="d8f66-112">générer un fichier de clé publique et de l'ajouter au fichier AssemblyInfo.cs ;</span><span class="sxs-lookup"><span data-stu-id="d8f66-112">Generate a public key file and add this file to the AssemblyInfo.cs file.</span></span>  
  
2.  <span data-ttu-id="d8f66-113">spécifier une version spécifique du fichier AssemblyInfo.cs.</span><span class="sxs-lookup"><span data-stu-id="d8f66-113">Specify a specific version in the AssemblyInfo.cs file.</span></span>  
  
 <span data-ttu-id="d8f66-114">Vous pouvez faire glisser l'assembly dans le Global Assembly Cache ou utiliser GACUTIL pour l'ajouter au GAC.</span><span class="sxs-lookup"><span data-stu-id="d8f66-114">You can either drag the assembly into the global assembly cache or use GACUTIL to add it to the global assembly cache.</span></span>  
  
 <span data-ttu-id="d8f66-115">Pour utiliser ce concepteur, indiquez le nom de classe complet, une virgule et l'entrée de l'assembly dans le Global Assembly Cache (nom de l'assembly, version, culture et jeton de clé publique) en tant que valeur de la décoration.</span><span class="sxs-lookup"><span data-stu-id="d8f66-115">To use this designer, specify the fully qualified class name, a comma, and the global assembly cache assembly entry (assembly name, version, culture, and public key token) as the value of the decoration.</span></span> <span data-ttu-id="d8f66-116">Utilisez \<éditeur > décorations pour **UITypeEditor** implémentations et \<convertisseur > décorations pour **TypeConverter** implémentations.</span><span class="sxs-lookup"><span data-stu-id="d8f66-116">Use \<editor> decorations for **UITypeEditor** implementations and \<converter> decorations for **TypeConverter** implementations.</span></span>  
  
 <span data-ttu-id="d8f66-117">Le code ci-dessous indique comment initialiser les concepteurs personnalisés dans un fichier XSD :</span><span class="sxs-lookup"><span data-stu-id="d8f66-117">The following code shows how to initialize the custom designers in an XSD file:</span></span>  
  
```  
<xs:element name="Global" type="xs:string">  
   <xs:annotation>  
      <xs:appinfo>  
         <baf:designer>  
            <baf:category>GAC Designer Component</baf:category>  
            <baf:editor>AdapterManagement.ComponentModel. PasswordUITypeEditor, AdapterManagement, Version=1.0.1.0, Culture=neutral, PublicKeyToken=f0db50abb0615c18</baf:editor>  
         </baf:designer>  
      </xs:appinfo>  
   </xs:annotation>  
</xs:element>  
      </xs:sequence>  
```  
  
## <a name="external-assembly-installation-and-use"></a><span data-ttu-id="d8f66-118">Installation et utilisation d'un assembly externe</span><span class="sxs-lookup"><span data-stu-id="d8f66-118">External Assembly Installation and Use</span></span>  
 <span data-ttu-id="d8f66-119">Pour les assemblys externes, la décoration contient un assembly d'attribut facultatif qui spécifie le chemin d'accès complet et le nom de l'assembly contenant le concepteur souhaité.</span><span class="sxs-lookup"><span data-stu-id="d8f66-119">For external assemblies, the decoration contains an optional attribute assembly that specifies the full path and name of the assembly containing the desired designer.</span></span>  
  
 <span data-ttu-id="d8f66-120">Le code ci-dessous indique comment initialiser les concepteurs personnalisés contenus dans des assemblys externes :</span><span class="sxs-lookup"><span data-stu-id="d8f66-120">The following code shows how to initialize the custom designers contained in external assemblies:</span></span>  
  
```  
<xs:element name="External" type="xs:string">  
   <xs:annotation>  
      <xs:appinfo>  
         <baf:designer>  
            <baf:category>External Designer Component</baf:category>  
            <baf:converter assembly="C:\source\private\Adapter\Framework\Designer\bin\Debug\Designer.External.dll">Designer.External.DesignerTypeConverter</baf:converter>  
         </baf:designer>  
      </xs:appinfo>  
   </xs:annotation>  
</xs:element>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d8f66-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8f66-121">See Also</span></span>  
 <span data-ttu-id="d8f66-122">[Éditeur de liste déroulante personnalisé pour la Configuration de l’adaptateur](../core/custom-drop-down-editor-for-adapter-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="d8f66-122">[Custom Drop-Down Editor for Adapter Configuration](../core/custom-drop-down-editor-for-adapter-configuration.md) </span></span>  
 <span data-ttu-id="d8f66-123">[Éditeur de boîte de dialogue modales personnalisé pour la Configuration de l’adaptateur](../core/custom-modal-dialog-editor-for-adapter-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="d8f66-123">[Custom Modal Dialog Editor for Adapter Configuration](../core/custom-modal-dialog-editor-for-adapter-configuration.md) </span></span>  
 <span data-ttu-id="d8f66-124">[Convertisseur de Type personnalisé pour la Configuration de l’adaptateur](../core/custom-type-converter-for-adapter-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="d8f66-124">[Custom Type Converter for Adapter Configuration](../core/custom-type-converter-for-adapter-configuration.md) </span></span>  
 [<span data-ttu-id="d8f66-125">Composants de Configuration avancée pour les cartes</span><span class="sxs-lookup"><span data-stu-id="d8f66-125">Advanced Configuration Components for Adapters</span></span>](../core/advanced-configuration-components-for-adapters.md)