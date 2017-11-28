---
title: "Décrire le schéma de Documentation WSDL PortType avec le Kit de développement logiciel de l’adaptateur LOB WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9dd96eaf-b3b3-49b4-aea9-0ae1e8999d62
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 038b8ca075e756a0857e70a420c0fc7913113c92
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="describe-the-wsdl-porttype-documentation-schema-with-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="402ac-102">Décrire le schéma de Documentation WSDL PortType avec le Kit de développement logiciel de l’adaptateur LOB WCF</span><span class="sxs-lookup"><span data-stu-id="402ac-102">Describe the WSDL PortType Documentation Schema with the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="402ac-103">Le fichier WSDL qui le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] génère contient des informations descriptives supplémentaires pour chaque type de port.</span><span class="sxs-lookup"><span data-stu-id="402ac-103">The WSDL that the  [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] generates contains additional descriptive information for each portType.</span></span> <span data-ttu-id="402ac-104">Le schéma pour plus d’informations est décrite dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="402ac-104">The schema for this additional information is described in this topic.</span></span>  
  
## <a name="documentation-xml-schema"></a><span data-ttu-id="402ac-105">Schéma XML de documentation</span><span class="sxs-lookup"><span data-stu-id="402ac-105">Documentation XML Schema</span></span>  
 <span data-ttu-id="402ac-106">La documentation de l’opération est implémentée à l’aide de l’annotation de type de port pour ajouter un nœud qui représente la documentation de l’adaptateur pour l’opération.</span><span class="sxs-lookup"><span data-stu-id="402ac-106">The operation documentation is implemented using annotation of the portType to add a node that represents the adapter documentation for the operation.</span></span> <span data-ttu-id="402ac-107">Ce nœud contient des sous-nœuds qui décrivent plus précisément l’opération et les paramètres.</span><span class="sxs-lookup"><span data-stu-id="402ac-107">This node contains subnodes that further describe the operation and parameters.</span></span> <span data-ttu-id="402ac-108">Ce schéma est défini comme suit.</span><span class="sxs-lookup"><span data-stu-id="402ac-108">This schema is defined as follows.</span></span>  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
\<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  \<xs:element name="adapterOperationDocumentation">  
    \<xs:complexType>  
      \<xs:sequence>  
        \<xs:element name="summary" type="xs:string" />  
        \<xs:element maxOccurs="unbounded" name="param">  
          \<xs:complexType>  
            \<xs:simpleContent>  
              \<xs:extension base="xs:string">  
                \<xs:attribute name="name" type="xs:string" use="required" />  
              \</xs:extension>  
            \</xs:simpleContent>  
          \</xs:complexType>  
        \</xs:element>  
        \<xs:element name="returns" type="xs:string" />  
      \</xs:sequence>  
    \</xs:complexType>  
  \</xs:element>  
\</xs:schema>  
```  
  
 <span data-ttu-id="402ac-109">Lorsque WSDL est généré pour une opération donnée, le schéma précédent est utilisé pour fournir des informations descriptives supplémentaires dans un format lisible.</span><span class="sxs-lookup"><span data-stu-id="402ac-109">When WSDL is generated for a given operation, the preceding schema is used to provide additional descriptive information in human readable format.</span></span> <span data-ttu-id="402ac-110">Par exemple, les informations de portType suivantes sont retournées pour l’opération EchoString de l’adaptateur de l’écho.</span><span class="sxs-lookup"><span data-stu-id="402ac-110">For example, the following portType information is returned for the EchoString operation of the Echo Adapter.</span></span>  
  
```  
\<wsdl:portType name="EchoService">  
  \<wsdl:operation name="EchoString">  
    \<wsdl:documentation>  
      \<doc:adapterOperationDocumentation>  
        \<doc:summary>String EchoString( string aName)\</doc:summary>  
        \<doc:param name="aName">This string will be echoed back to the user.\</doc:param>  
        \<doc:returns>String value containing the value of aName \</doc:returns>  
      \</doc:adapterOperationDocumentation>  
    \</wsdl:documentation>  
    \<wsdl:input wsaw:Action="Echo/EchoString" message="ns2:EchoService_EchoString_InputMessage" />  
    \<wsdl:output wsaw:Action="Echo/EchoString/response" message="ns2:EchoService_EchoString_OutputMessage" />  
  \</wsdl:operation>  
\</wsdl:portType>  
```  
  
 <span data-ttu-id="402ac-111">Les valeurs pour les éléments de la documentation sont obtenues à partir de `Microsoft.ServiceModel.Channels.Common.ParameterizedOperationMetadata` pour l’opération.</span><span class="sxs-lookup"><span data-stu-id="402ac-111">The values for the documentation elements are obtained from `Microsoft.ServiceModel.Channels.Common.ParameterizedOperationMetadata` for the operation.</span></span> <span data-ttu-id="402ac-112">L’exemple précédent a été générée en raison de l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="402ac-112">The preceding example was generated as a result of the following example.</span></span>  
  
```csharp  
ParameterizedOperationMetadata om = new ParameterizedOperationMetadata(operationId, operationId);  
// set this if you want this operation to belong to this interface name  
// in the generated proxy, the interface name will be EchoService  
// and the client implementation name will be EchoServiceClient.  
om.OperationGroup = "EchoService";  
// set the operation namespace to be same as service namespace  
om.OperationNamespace = EchoAdapter.SERVICENAMESPACE;              
switch (operationId)  
{  
   case "Echo/EchoString":  
       om.DisplayName = "EchoString";  
       om.OriginalName = "targetSystemEchoString";  
       om.Description = "String EchoString( string aName)";  
       OperationParameter parm1 = new OperationParameter("aName", OperationParameterDirection.In, QualifiedType.StringType, false);  
       parm1.Description = "This string will be echoed back to the user.";  
       OperationResult result = new OperationResult(new SimpleQualifiedType(XmlTypeCode.String), false);  
       result.Description = "String value containing the value of aName";  
       om.Parameters.Add(parm1);  
       om.OperationResult = result;  
       return om;   
```  
  
## <a name="see-also"></a><span data-ttu-id="402ac-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="402ac-113">See Also</span></span>  
 [<span data-ttu-id="402ac-114">Recommandées de développement à l’aide de WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="402ac-114">Development best practices using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/development-best-practices-using-the-wcf-lob-adapter-sdk.md)