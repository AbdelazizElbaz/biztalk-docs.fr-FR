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
ms.openlocfilehash: 81e4977403da18229aea19beef21f361dfdd9391
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="describe-the-wsdl-porttype-documentation-schema-with-the-wcf-lob-adapter-sdk"></a>Décrire le schéma de Documentation WSDL PortType avec le Kit de développement logiciel de l’adaptateur LOB WCF
Le fichier WSDL qui le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] génère contient des informations descriptives supplémentaires pour chaque type de port. Le schéma pour plus d’informations est décrite dans cette rubrique.  
  
## <a name="documentation-xml-schema"></a>Schéma XML de documentation  
 La documentation de l’opération est implémentée à l’aide de l’annotation de type de port pour ajouter un nœud qui représente la documentation de l’adaptateur pour l’opération. Ce nœud contient des sous-nœuds qui décrivent plus précisément l’opération et les paramètres. Ce schéma est défini comme suit.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="adapterOperationDocumentation">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="summary" type="xs:string" />  
        <xs:element maxOccurs="unbounded" name="param">  
          <xs:complexType>  
            <xs:simpleContent>  
              <xs:extension base="xs:string">  
                <xs:attribute name="name" type="xs:string" use="required" />  
              </xs:extension>  
            </xs:simpleContent>  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="returns" type="xs:string" />  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
 Lorsque WSDL est généré pour une opération donnée, le schéma précédent est utilisé pour fournir des informations descriptives supplémentaires dans un format lisible. Par exemple, les informations de portType suivantes sont retournées pour l’opération EchoString de l’adaptateur de l’écho.  
  
```  
<wsdl:portType name="EchoService">  
  <wsdl:operation name="EchoString">  
    <wsdl:documentation>  
      <doc:adapterOperationDocumentation>  
        <doc:summary>String EchoString( string aName)\</doc:summary>  
        <doc:param name="aName">This string will be echoed back to the user.\</doc:param>  
        <doc:returns>String value containing the value of aName \</doc:returns>  
      </doc:adapterOperationDocumentation>  
    </wsdl:documentation>  
    <wsdl:input wsaw:Action="Echo/EchoString" message="ns2:EchoService_EchoString_InputMessage" />  
    <wsdl:output wsaw:Action="Echo/EchoString/response" message="ns2:EchoService_EchoString_OutputMessage" />  
  </wsdl:operation>  
</wsdl:portType>  
```  
  
 Les valeurs pour les éléments de la documentation sont obtenues à partir de `Microsoft.ServiceModel.Channels.Common.ParameterizedOperationMetadata` pour l’opération. L’exemple précédent a été générée en raison de l’exemple suivant.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Recommandées de développement à l’aide de WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/development-best-practices-using-the-wcf-lob-adapter-sdk.md)