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
# <a name="examples-of-custom-configuration-schemas-for-adapters"></a><span data-ttu-id="79780-102">Exemples de schémas de Configuration personnalisée pour les adaptateurs</span><span class="sxs-lookup"><span data-stu-id="79780-102">Examples of Custom Configuration Schemas for Adapters</span></span>
<span data-ttu-id="79780-103">Cette section fournit les exemples suivants de personnalisation de schémas de configuration pour les adaptateurs : </span><span class="sxs-lookup"><span data-stu-id="79780-103">This section provides the following examples for how to customize configuration schemas for adapters:</span></span>  
  
-   <span data-ttu-id="79780-104">**Exemple 1** montre un fichier de schéma XSD personnalisé complet représentant une page de propriétés de l’adaptateur avec les extensions baf : Designer et baf : description.</span><span class="sxs-lookup"><span data-stu-id="79780-104">**Example 1** shows a complete custom XSD schema file representing an adapter property page using the baf:designer and baf:description extensions.</span></span>  
  
-   <span data-ttu-id="79780-105">**Exemple 2** utilise également les extensions baf : Designer et baf : description pour montrer comment créer une fenêtre de valeur de propriété personnalisée pour le **BatchSize** propriété qui accepte uniquement les valeurs comprises entre 1 et 99 inclus.</span><span class="sxs-lookup"><span data-stu-id="79780-105">**Example 2** also uses the baf:designer and baf:description extensions to show how to create a custom property value window for the **BatchSize** property that only accepts values between 1 and 99, inclusive.</span></span>  
  
-   <span data-ttu-id="79780-106">**Exemple 3** montre comment limiter baf : Password à 8 caractères.</span><span class="sxs-lookup"><span data-stu-id="79780-106">**Example 3** shows how to limit the baf:Password to 8 characters.</span></span> <span data-ttu-id="79780-107">Par défaut, 22 caractères sont possibles.</span><span class="sxs-lookup"><span data-stu-id="79780-107">By default, it allows 22 characters.</span></span>  
  
-   <span data-ttu-id="79780-108">**Exemple 4** montre comment implémenter des contraintes de critères spéciaux sur les valeurs de propriété, car les modèles XSD ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="79780-108">**Example 4** shows how to implement pattern-matching constraints on property values because XSD patterns are not supported.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="79780-109">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="79780-109">Example 1</span></span>  
 <span data-ttu-id="79780-110">Cet exemple illustre un schéma XSD personnalisé complet.</span><span class="sxs-lookup"><span data-stu-id="79780-110">This example shows a complete custom XSD schema.</span></span> <span data-ttu-id="79780-111">Il représente une page de propriété d'adaptateur avec les extensions baf:designer et baf:description.</span><span class="sxs-lookup"><span data-stu-id="79780-111">It represents an adapter property page using the baf:designer and baf:description extensions.</span></span>  
  
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
  
## <a name="example-2"></a><span data-ttu-id="79780-112">Exemple 2</span><span class="sxs-lookup"><span data-stu-id="79780-112">Example 2</span></span>  
 <span data-ttu-id="79780-113">Cet exemple utilise les extensions baf : Designer et baf : description pour montrer comment créer une fenêtre de valeur de propriété personnalisée pour le **BatchSize** propriété qui accepte uniquement les valeurs comprises entre 1 et 99 inclus.</span><span class="sxs-lookup"><span data-stu-id="79780-113">This example uses the baf:designer and baf:description extensions to show how to create a custom property value window for the **BatchSize** property that only accepts values between 1 and 99, inclusive.</span></span>  
  
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
  
## <a name="example-3"></a><span data-ttu-id="79780-114">Exemple 3</span><span class="sxs-lookup"><span data-stu-id="79780-114">Example 3</span></span>  
 <span data-ttu-id="79780-115">Cet exemple montre comment limiter baf:Password à 8 caractères.</span><span class="sxs-lookup"><span data-stu-id="79780-115">This example shows how to limit the baf:Password to 8 characters.</span></span> <span data-ttu-id="79780-116">Par défaut, 22 caractères sont possibles.</span><span class="sxs-lookup"><span data-stu-id="79780-116">By default, it allows 22 characters.</span></span>  
  
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
  
## <a name="example-4"></a><span data-ttu-id="79780-117">Exemple 4</span><span class="sxs-lookup"><span data-stu-id="79780-117">Example 4</span></span>  
 <span data-ttu-id="79780-118">Cet exemple montre comment implémenter des contraintes de critères spéciaux sur les valeurs de propriété car les modèles XSD ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="79780-118">This example shows how to implement pattern-matching constraints on property values because XSD patterns are not supported.</span></span>  
  
 <span data-ttu-id="79780-119">Les champs tels que **ClientIdentifier** sont toujours une chaîne de trois caractères numérique.</span><span class="sxs-lookup"><span data-stu-id="79780-119">Fields such as **ClientIdentifier** are always a three-character numeric string.</span></span> <span data-ttu-id="79780-120">La valeur de propriété 10 ne sera pas correcte, mais la valeur 010 si.</span><span class="sxs-lookup"><span data-stu-id="79780-120">A property value of 10 is not valid, whereas 010 is valid.</span></span> <span data-ttu-id="79780-121">Le fragment de schéma de configuration suivant définit un **ClientIdentifier** propriété.</span><span class="sxs-lookup"><span data-stu-id="79780-121">The following configuration schema fragment defines a **ClientIdentifier** property.</span></span> <span data-ttu-id="79780-122">Le **ClientIdentifierConverter** (classe), implémentée dans votre assembly d’adaptateur, implémente la recherche de correspondance.</span><span class="sxs-lookup"><span data-stu-id="79780-122">The **ClientIdentifierConverter** class, implemented in your adapter assembly, implements pattern matching.</span></span> <span data-ttu-id="79780-123">Dans le cas présent, le convertisseur de type personnalisé restreint les valeurs à une chaîne d'exactement trois chiffres (000 à 999).</span><span class="sxs-lookup"><span data-stu-id="79780-123">In this case, the custom type converter restricts values to a string of exactly three digits (000 to 999).</span></span> <span data-ttu-id="79780-124">Dans le schéma de configuration, assurez-vous que l'assembly et le nom complet du type pour le nœud baf:converter sont correctement définis.</span><span class="sxs-lookup"><span data-stu-id="79780-124">In the configuration schema, make sure the baf:converter node has the assembly and type full name set correctly.</span></span> <span data-ttu-id="79780-125">Si l'utilisateur tente d'entrer une valeur incorrecte, un message s'affiche dès qu'une erreur de validation se produit dans la page de propriétés.</span><span class="sxs-lookup"><span data-stu-id="79780-125">If the user attempts to enter a value that is not valid, an exception message pops up when a validation error occurs in the property page.</span></span>  
  
 <span data-ttu-id="79780-126">Vous pouvez employer le code suivant dans les schémas de configuration de la page de propriétés de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="79780-126">You can use the following code in the adapter property page configuration schemas.</span></span>  
  
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
  
 <span data-ttu-id="79780-127">Vous pouvez intégrer le code suivant dans l'assembly de votre adaptateur.</span><span class="sxs-lookup"><span data-stu-id="79780-127">You can place the following code in your adapter assembly.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="79780-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79780-128">See Also</span></span>  
 [<span data-ttu-id="79780-129">Extensions de schéma de Configuration Framework adaptateur</span><span class="sxs-lookup"><span data-stu-id="79780-129">Adapter Framework Configuration Schema Extensions</span></span>](../core/adapter-framework-configuration-schema-extensions.md)