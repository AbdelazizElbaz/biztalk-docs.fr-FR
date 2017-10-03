---
title: "L’activation des Extensions de Configuration Framework adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 851f4a20-502d-45f8-9647-13bec33fa460
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 346bbc3d4d136ad7116a68b3c57a47566f258a68
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="enabling-adapter-framework-configuration-extensions"></a><span data-ttu-id="c4396-102">L’activation des Extensions Configuration infrastructure d’adaptateurs</span><span class="sxs-lookup"><span data-stu-id="c4396-102">Enabling Adapter Framework Configuration Extensions</span></span>
<span data-ttu-id="c4396-103">L'infrastructure d'adaptateurs BizTalk fournit plusieurs extensions permettant d'améliorer l'utilisation.</span><span class="sxs-lookup"><span data-stu-id="c4396-103">The BizTalk Adapter Framework provides several extensions to improve the user experience.</span></span> <span data-ttu-id="c4396-104">Pour utiliser ces extensions, importez le schéma de l’infrastructure, BiztalkAdapterFramework.xsd.</span><span class="sxs-lookup"><span data-stu-id="c4396-104">To use these extensions, import the framework's schema, BiztalkAdapterFramework.xsd.</span></span> <span data-ttu-id="c4396-105">Importation du schéma vous permet à des décorations et types spécifiques et de les utiliser dans le schéma de configuration de l’adaptateur, comme décrit ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="c4396-105">Importing the schema enables you to access decorations and specialized types and to use them in the adapter's configuration schema, as described below.</span></span> <span data-ttu-id="c4396-106">Le code suivant montre comment importer le schéma :</span><span class="sxs-lookup"><span data-stu-id="c4396-106">The following code shows how to import the schema:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?><xs:schema   targetNamespace="http://tempuri.org/XMLSchema.xsd"   
         elementFormDefault="qualified" xmlns="http://tempuri.org/XMLSchema.xsd"   
         xmlns:baf="BiztalkAdapterFramework.xsd"   
         xmlns:xs="http://www.w3.org/2001/XMLSchema"   
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:import namespace="BiztalkAdapterFramework.xsd" />  
. . .  
</xs:schema>  
```  
  
## <a name="importing-the-biztalk-adapter-framework-extensions-schema-xsd"></a><span data-ttu-id="c4396-107">Importation du schéma XSD des Extensions de l'infrastructure d'adaptateurs BizTalk</span><span class="sxs-lookup"><span data-stu-id="c4396-107">Importing the BizTalk Adapter Framework Extensions Schema XSD</span></span>  
 <span data-ttu-id="c4396-108">En important le schéma XSD des extensions infrastructure d’adaptateurs, vous pouvez utiliser des décorations telles que \<baf : filename > comme type d’élément, qui indique le nom de fichier contextuelle lors de la modification de l’élément.</span><span class="sxs-lookup"><span data-stu-id="c4396-108">By importing the Adapter Framework extensions schema XSD, you can use decorations such as \<baf:FileName> as an element's type, which shows the file name pop-up when editing the element.</span></span>  
  
 <span data-ttu-id="c4396-109">D'autres décorations contrôlent l'affichage de la propriété dans l'interface.</span><span class="sxs-lookup"><span data-stu-id="c4396-109">Additional decorations control the display of the property in the interface.</span></span> <span data-ttu-id="c4396-110">Le \<baf : description > décoration, ajoute, par exemple, le texte d’aide à l’élément.</span><span class="sxs-lookup"><span data-stu-id="c4396-110">The \<baf:description> decoration, for example, adds help text to the element.</span></span> <span data-ttu-id="c4396-111">Le \<baf : description > affiche le texte en bas de la page de propriétés.</span><span class="sxs-lookup"><span data-stu-id="c4396-111">The \<baf:description> decoration displays the text at the bottom of the property page.</span></span> <span data-ttu-id="c4396-112">Le \<baf : browsable > décoration masque un élément de l’interface.</span><span class="sxs-lookup"><span data-stu-id="c4396-112">The \<baf:browsable> decoration hides an element from the interface.</span></span> <span data-ttu-id="c4396-113">Le code suivant montre comment utiliser ces éléments dans un schéma de configuration :</span><span class="sxs-lookup"><span data-stu-id="c4396-113">The following code shows how you can use these elements within a configuration schema:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?><xs:schema   targetNamespace="http://tempuri.org/XMLSchema.xsd"   
         elementFormDefault="qualified" xmlns="http://tempuri.org/XMLSchema.xsd"   
         xmlns:baf="BiztalkAdapterFramework.xsd"   
         xmlns:xs="http://www.w3.org/2001/XMLSchema"   
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:import namespace="BiztalkAdapterFramework.xsd" />  
   <xs:element name="Send">  
      <xs:complexType>  
         <xs:sequence>  
            <xs:element name="directory" type="xs:string" />  
               <xs:annotation>  
                  <xs:appinfo>  
                     <baf:designer>  
                        <baf:description>Enter the directory that will receive sent files..  
                        </baf:description>  
                     </baf:designer>  
                  </xs:appinfo>  
               </xs:annotation>  
            </xs:element>  
            <xs:element name="fileName" type="" />  
            <xs:element name="sendBatchSize" type="xs:int" />  
            <xs:element name="fileCopyMode" type="CopyMode" />  
            <xs:element name="uri" type="xs:string" >  
               <xs:annotation>  
                  <xs:appinfo>  
                     <baf:designer>  
                        <baf:browsable show="false" />  
                     </baf:designer>  
                  </xs:appinfo>  
               </xs:annotation>  
            </xs:element>  
         </xs:sequence>  
      </xs:complexType>  
   </xs:element>  
   <xs:simpleType name="CopyMode">  
      <xs:restriction base="xs:string">  
         <xs:enumeration value="Append">  
            <xs:annotation>  
               <xs:documentation>= 0</xs:documentation>  
            </xs:annotation>  
         <xs:enumeration value="Create">  
            <xs:annotation>  
               <xs:documentation>= 1</xs:documentation>  
            </xs:annotation>  
         <xs:enumeration value="CreateNew">  
            <xs:annotation>  
               <xs:documentation>= 2</xs:documentation>  
            </xs:annotation>  
         </xs:enumeration>  
      </xs:restriction>  
   </xs:simpleType>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c4396-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4396-114">See Also</span></span>  
 [<span data-ttu-id="c4396-115">Extensions de schéma de Configuration Framework adaptateur</span><span class="sxs-lookup"><span data-stu-id="c4396-115">Adapter Framework Configuration Schema Extensions</span></span>](../core/adapter-framework-configuration-schema-extensions.md)