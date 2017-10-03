---
title: "Exemples de schémas de Configuration personnalisée pour les adaptateurs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31b188de-9363-4f4c-b40a-149ff59ddf8d
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b11cb16c7b7ae9285b6ffb77c7177964d211482f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="examples-of-custom-configuration-schemas-for-adapters"></a>Exemples de schémas de Configuration personnalisée pour les adaptateurs
Cette section fournit les exemples suivants de personnalisation de schémas de configuration pour les adaptateurs :   
  
-   **Exemple 1** montre un fichier de schéma XSD personnalisé complet représentant une page de propriétés de l’adaptateur avec les extensions baf : Designer et baf : description.  
  
-   **Exemple 2** utilise également les extensions baf : Designer et baf : description pour montrer comment créer une fenêtre de valeur de propriété personnalisée pour le **BatchSize** propriété qui accepte uniquement les valeurs comprises entre 1 et 99 inclus.  
  
-   **Exemple 3** montre comment limiter baf : Password à 8 caractères. Par défaut, 22 caractères sont possibles.  
  
-   **Exemple 4** montre comment implémenter des contraintes de critères spéciaux sur les valeurs de propriété, car les modèles XSD ne sont pas pris en charge.  
  
## <a name="example-1"></a>Exemple 1  
 Cet exemple illustre un schéma XSD personnalisé complet. Il représente une page de propriété d'adaptateur avec les extensions baf:designer et baf:description.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<xs:schema   targetNamespace="http://tempuri.org/XMLSchema.xsd"   
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
  
## <a name="example-2"></a>Exemple 2  
 Cet exemple utilise les extensions baf : Designer et baf : description pour montrer comment créer une fenêtre de valeur de propriété personnalisée pour le **BatchSize** propriété qui accepte uniquement les valeurs comprises entre 1 et 99 inclus.  
  
```  
   <xs:element name="BatchSize">  
          <xs:simpleType>  
            <xs:annotation>  
              <xs:appinfo>  
                <baf:designer>  
                  <baf:displayname>Batch Size</baf:displayname>  
                  <baf:description>Enter the batch size (1-99)</baf:description>  
                </baf:designer>  
              </xs:appinfo>  
            </xs:annotation>  
            <xs:restriction base="xs:int">  
              <xs:minInclusive value="1" />  
              <xs:maxInclusive value="99" />  
            </xs:restriction>  
          </xs:simpleType>  
        </xs:element>  
```  
  
## <a name="example-3"></a>Exemple 3  
 Cet exemple montre comment limiter baf:Password à 8 caractères. Par défaut, 22 caractères sont possibles.  
  
```  
<xs:element name="AdapterPassword">  
          <xs:simpleType>  
            <xs:annotation>  
              <xs:appinfo>  
                <baf:designer>  
                  <baf:displayname>Adapter Password</baf:displayname>  
                  <baf:description>Enter the password (up to 8 characters)</baf:description>  
                  <baf:editor assembly="%BTSROOT%\\Developer Tools\\Microsoft.BizTalk.Adapter.Framework.dll">Microsoft.BizTalk.Adapter.Framework.ComponentModel.PasswordUITypeEditor</baf:editor>  
                  <baf:converter assembly="%BTSROOT%\\Developer Tools\\Microsoft.BizTalk.Adapter.Framework.dll">Microsoft.BizTalk.Adapter.Framework.ComponentModel.PasswordTypeConverter</baf:converter>  
                </baf:designer>  
              </xs:appinfo>  
            </xs:annotation>  
            <xs:restriction base="xs:string">  
              <xs:maxLength value="8" />  
            </xs:restriction>  
          </xs:simpleType>  
        </xs:element>  
```  
  
## <a name="example-4"></a>Exemple 4  
 Cet exemple montre comment implémenter des contraintes de critères spéciaux sur les valeurs de propriété car les modèles XSD ne sont pas pris en charge.  
  
 Les champs tels que **ClientIdentifier** sont toujours une chaîne de trois caractères numérique. La valeur de propriété 10 ne sera pas correcte, mais la valeur 010 si. Le fragment de schéma de configuration suivant définit un **ClientIdentifier** propriété. Le **ClientIdentifierConverter** (classe), implémentée dans votre assembly d’adaptateur, implémente la recherche de correspondance. Dans le cas présent, le convertisseur de type personnalisé restreint les valeurs à une chaîne d'exactement trois chiffres (000 à 999). Dans le schéma de configuration, assurez-vous que l'assembly et le nom complet du type pour le nœud baf:converter sont correctement définis. Si l'utilisateur tente d'entrer une valeur incorrecte, un message s'affiche dès qu'une erreur de validation se produit dans la page de propriétés.  
  
 Vous pouvez employer le code suivant dans les schémas de configuration de la page de propriétés de l'adaptateur.  
  
```  
        <xs:element name="ClientIdentifier" type="xs:string">  
          <xs:annotation>  
            <xs:appinfo>  
              <baf:designer>  
                <baf:displayname>Adapter Client</baf:displayname>  
                <baf:description>Enter the Adapter Client (3 digit string)</baf:description>  
                <baf:converter assembly="%BTSROOT%\\Developer Tools\\Microsoft.BizTalk.TestAdapter.dll">Microsoft.BizTalk.TestAdapter.ClientIdentifierConverter</baf:converter>  
              </baf:designer>  
            </xs:appinfo>  
          </xs:annotation>  
        </xs:element>  
```  
  
 Vous pouvez intégrer le code suivant dans l'assembly de votre adaptateur.  
  
```  
using System;  
using System.ComponentModel;  
using System.Globalization;  
using System.Text.RegularExpressions;  
  
namespace Microsoft.BizTalk.TestAdapter  
{  
       /// <summary>  
       /// Summary description for ClientIdentifierConverter.  
       /// </summary>  
       public class ClientIdentifierConverter : System.ComponentModel.StringConverter   
       {  
              private void Validate(string value)  
              {  
                     Regex regex = new Regex(@"^\d{3}$"); // ^=begin, \d=digit, {3}=exactly 3 occurrences, $=end  
                     Match match = regex.Match((string)value);  
                     if (!match.Success)  
                     {  
                           throw new ApplicationException("Value does not match pattern \"" + regex.ToString() + "\".");  
                     }  
              }  
  
              public override object ConvertFrom(ITypeDescriptorContext context, CultureInfo culture, object value)  
              {  
                     if (value is string)  
                     {  
                           this.Validate((string)value);  
                     }  
                     return base.ConvertFrom(context, culture, value);  
              }  
  
              public override object ConvertTo(ITypeDescriptorContext context, CultureInfo culture, object value, Type destinationType)  
              {  
                     if (typeof(string) == destinationType && value is string)  
                     {  
                           this.Validate((string)value);  
                     }  
                     return base.ConvertTo(context, culture, value, destinationType);  
              }  
       }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Extensions de schéma de Configuration Framework adaptateur](../core/adapter-framework-configuration-schema-extensions.md)