---
title: "Schémas de Configuration de carte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc08fa71-c5f7-4365-9506-e02351b17567
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 89ca7d02c756fdbdf819e1a15069a95d0784d764
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="adapter-configuration-schemas"></a>Schémas de configuration de l'adaptateur
Différents types de schémas sont utilisés pour la configuration de la conception d'un adaptateur. En fonction de la visibilité et de l'étendue des valeurs de propriété, divers schémas sont modifiés et utilisés.  
  
## <a name="handler-schemas"></a>Schémas de gestionnaire  
 La configuration de l'adaptateur fournie par un gestionnaire s'applique à l'adaptateur et à tous ses consommateurs dans une étendue globale. Un administrateur peut modifier de manière statique la configuration d'un gestionnaire au moment de la conception en utilisant la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour développer le gestionnaire de réception ou d'envoi de l'adaptateur et afficher les propriétés de l'hôte spécifié.  
  
 L'exemple de l'adaptateur File du kit de développement logiciel (SDK) comporte un ensemble de fichiers XSD utilisés pour configurer son emplacement de réception, son port d'envoi, son gestionnaire de réception et son gestionnaire d'envoi. Modifiez ces fichiers XSD de sorte que votre adaptateur personnalisé reçoive les propriétés de configuration qu'il requiert. Les fichiers que vous devez modifier dans l'exemple d'adaptateur File sont les fichiers de schéma TransmitHandler.xsd et ReceiveHandler.xsd. Ces fichiers configurent respectivement le gestionnaire d'envoi et le gestionnaire de réception, en contrôlant les pages de propriétés utilisées pour configurer les gestionnaires dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 À l'aide de vos exigences d'adaptateur, créez une liste des propriétés de configuration requises pour chacun des points de terminaison. Si l'ensemble de ces propriétés sont globales, vous n'aurez sans doute qu'à modifier les configurations des ports d'envoi et des ports de réception. Si les propriétés de l'adaptateur doivent être définies pour chaque port d'envoi ou emplacement de réception, il vous faudra également modifier les fichiers de configuration d'emplacement de réception et de port d'envoi.   
  
 L'infrastructure d'adaptateurs fournit des extensions de schéma et des options avancées de configuration prenant en charge les conditions requises communes pour la configuration des adaptateurs. Elle fournit de plus des extensions qui ne figurent pas dans le schéma inclus avec l'exemple d'adaptateur FILE. Pour plus d’informations sur les extensions de schéma d’infrastructure d’adaptateurs, consultez [Extensions de schéma de Configuration Framework adaptateur](../core/adapter-framework-configuration-schema-extensions.md). Pour plus d’informations sur les options de configuration avancées telles que les éditeurs déroulants personnalisés et les convertisseurs de type personnalisé, consultez [des composants de Configuration avancée pour les adaptateurs](../core/advanced-configuration-components-for-adapters.md).  
  
 Le code qui figure à la fin de cette rubrique est issu du fichier TransmitHandler.xsd. Il génère la page de propriétés suivante.  
  
 ![](../core/media/ebiz-prog-custad-sh.gif "ebiz_prog_custad_sh")  
Page de propriétés du gestionnaire d'envoi, créée par le fichier TransmitHandler.xsd  
  
 Notez l’utilisation de la \<Designer\>, \<baf : DisplayName\>, et \<baf : description\> balises dans le code TransmitHandler.xsd présenté ci-dessous. Il s'agit de décorations personnalisées fournies par l'infrastructure d'adaptateurs pour accélérer la génération des pages de propriétés.  
  
 Pour obtenir la liste de toutes les décorations disponibles pour une utilisation dans l’infrastructure d’adaptateurs, consultez [balises d’ornement adaptateur Framework Configuration schéma](../core/adapter-framework-configuration-schema-decoration-tags.md).  
  
 Notez que le schéma ne comporte qu'un élément et qu'il ne contient aucun élément URI.  
  
> [!IMPORTANT]
>  Ne stockez pas de données sensibles relatives aux clients dans le schéma d'adaptateur par défaut. Pour des raisons de sécurité, il est recommandé de configurer le nom d'utilisateur et le mot de passe uniquement après avoir déployé un adaptateur. Cela garantit que les informations sont bien stockées dans la base de données de l'authentification unique de l'entreprise. Pour plus d’informations sur la base de données SSO, consultez [à l’aide de l’authentification unique](../core/using-sso.md).  
  
```  
<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:baf="BiztalkAdapterFramework.xsd"   
xmlns:b="http://schemas.microsoft.com/BizTalk/2003"   
xmlns="http://tempuri.org/XMLSchema1.xsd"   
elementFormDefault="qualified" targetNamespace="http://tempuri.org/XMLSchema1.xsd"   
id="TransmitHandler" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="Config">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element default="50" name="sendBatchSize" type="xs:int" >  
      <xs:annotation>  
         <xs:appinfo>  
            <baf:designer>  
               <baf:displayname _locID="sendBatchSizeName">Batch Size</baf:displayname>  
               <baf:description _locID="sendBatchSizeDesc">Enter the   
maximum number of files to be transmitted per batch</baf:description>  
            </baf:designer>  
         </xs:appinfo>  
      </xs:annotation>  
   </xs:element>  
  
        <xs:element default="4096" name="bufferSize" type="xs:int" >  
      <xs:annotation>  
         <xs:appinfo>  
            <baf:designer>  
               <baf:displayname _locID="bufferSizeName">Write Buffer Size</baf:displayname>  
               <baf:description _locID="bufferSizeDesc">Enter the size of   
the buffer used to write the file</baf:description>  
            </baf:designer>  
         </xs:appinfo>  
      </xs:annotation>  
   </xs:element>  
  
        <xs:element default="1" name="threadsPerCPU" type="xs:int" >  
      <xs:annotation>  
         <xs:appinfo>  
            <baf:designer>  
               <baf:displayname _locID="threadsPerCPUName">Threads Per CPU</baf:displayname>  
               <baf:description _locID="threadsPerCPUDesc">Enter the   
number of threads per CPU to execute in the thread pool</baf:description>  
            </baf:designer>  
         </xs:appinfo>  
      </xs:annotation>  
   </xs:element>  
  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
## <a name="send-port-and-receive-location-schemas"></a>Schémas du port d'envoi et de l'emplacement de réception  
 Pour définir des propriétés spécifiques aux ports de votre adaptateur, modifiez les schémas de configuration de l'emplacement de réception et du port d'envoi. Les fichiers de schéma TransmitLocation.xsd et ReceiveLocation.xsd configurent le port d'envoi et l'emplacement de réception respectivement.  
  
 L'infrastructure d'adaptateurs fournit des extensions de schéma et des options avancées de configuration prenant en charge les conditions requises communes pour la configuration des adaptateurs. Pour plus d’informations sur les extensions de schéma d’infrastructure d’adaptateurs, consultez [Extensions de schéma de Configuration Framework adaptateur](../core/adapter-framework-configuration-schema-extensions.md). Pour plus d’informations sur les options de configuration avancées telles que les éditeurs déroulants personnalisés et les convertisseurs de type personnalisé, consultez [des composants de Configuration avancée pour les adaptateurs](../core/advanced-configuration-components-for-adapters.md).  
  
 Le code qui suit est issu du fichier TransmitLocation.xsd. Il génère la page de propriétés suivante.  
  
 ![](../core/media/ebiz-prog-custad-sp.gif "ebiz_prog_custad_sp")  
Illustration de la page de propriétés du port d'envoi de l'exemple d'adaptateur FILE.  
  
 Notez que, dans le fichier TransmitLocation.xsd ci-dessous que la configuration du port d’envoi contient le \<Designer\>, \<baf : DisplayName\>, et \<baf : description\> des balises, comme le Gestionnaire d’envoi, il utilise également le \<baf : category\> balise. La balise « category » vous permet de regrouper les propriétés. Si vous avez plus d'une catégorie, chacune peut être développée ou réduite et apparaît sous la forme d'un en-tête gris au-dessus des propriétés qui lui correspondent. Pour plus d’informations, consultez [Extensions de schéma de Configuration Framework adaptateur](../core/adapter-framework-configuration-schema-extensions.md).  
  
 Ce schéma contient également un champ URI. Il est renseigné dans la page qui apparaît une fois que vous avez entré toutes les informations de champ dans la page des propriétés du port d'envoi au cours du traitement de validation effectué par l'adaptateur.  
  
```  
<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:baf="BiztalkAdapterFramework.xsd" xmlns:b="http://schemas.microsoft.com/BizTalk/2003" xmlns="http://tempuri.org/XMLSchema1.xsd" elementFormDefault="qualified" targetNamespace="http://tempuri.org/XMLSchema1.xsd" id="TransmitLocation" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="Config">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="directory" type="xs:string">  
      <xs:annotation>  
         <xs:appinfo>  
            <baf:designer xmlns:baf="BiztalkAdapterFramework.xsd">  
               <baf:displayname _locID="sendDirectoryName">Directory</baf:displayname>  
               <baf:description _locID="sendDirectoryDesc">Directory to write the file to</baf:description>  
                         <baf:category _locID="transmitLocationCategory">Transmit Location</baf:category>  
                    </baf:designer>  
         </xs:appinfo>  
      </xs:annotation>  
        </xs:element>  
  
        <xs:element default="%MessageID%.xml" name="fileName" type="xs:string">  
          <xs:annotation>  
            <xs:appinfo>  
              <baf:designer xmlns:baf="BiztalkAdapterFramework.xsd">  
                <baf:displayname _locID="fileNameName">File Name</baf:displayname>  
      <baf:description _locID="fileNameDesc">The name of the file that will be written</baf:description>  
                <baf:category _locID="transmitLocationCategory">Transmit Location</baf:category>  
              </baf:designer>  
            </xs:appinfo>  
          </xs:annotation>  
        </xs:element>  
  
        <xs:element default="2" name="fileCopyMode" type="CopyMode">  
          <xs:annotation>  
            <xs:appinfo>  
              <baf:designer xmlns:baf="BiztalkAdapterFramework.xsd">  
                <baf:displayname _locID="fileCopyModeName">File Mode</baf:displayname>  
                <baf:category _locID="transmitLocationCategory">Transmit Location</baf:category>  
              </baf:designer>  
            </xs:appinfo>  
          </xs:annotation>  
        </xs:element>  
  
        <xs:element name="uri" type="xs:string">  
          <xs:annotation>  
            <xs:appinfo>  
              <baf:designer xmlns:baf="BiztalkAdapterFramework.xsd">  
                <baf:browsable show="false" />  
              </baf:designer>  
            </xs:appinfo>  
          </xs:annotation>  
        </xs:element>  
  
   <!-- An example of how an SSO affiliate application would be configured for this endpoint: -->  
   <!--  
   <xs:element name="ssoAffiliateApplication" type="baf:SSOList">  
      <xs:annotation>  
         <xs:appinfo>  
            <baf:designer>  
               <baf:displayname _locID="ssoAffiliateApplicationName">SSO Affiliate</baf:displayname>  
               <baf:description _locID="ssoAffiliateApplicationDesc">The Single Sign On (SSO) Affiliate Application</baf:description>  
               <baf:category _locID="ftpCategory">FTP</baf:category>  
            </baf:designer>  
         </xs:appinfo>  
      </xs:annotation>  
   </xs:element>  
   -->  
  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
  
  <xs:simpleType name="CopyMode">  
    <xs:restriction base="xs:int">  
      <xs:enumeration value="0">  
        <xs:annotation>  
          <xs:appinfo>  
            <baf:designer xmlns:baf="BiztalkAdapterFramework.xsd">  
              <baf:displayname _locID="appendName">Append</baf:displayname>  
            </baf:designer>  
          </xs:appinfo>  
        </xs:annotation>  
      </xs:enumeration>  
      <xs:enumeration value="1">  
        <xs:annotation>  
          <xs:appinfo>  
            <baf:designer xmlns:baf="BiztalkAdapterFramework.xsd">  
              <baf:displayname _locID="createName">Create</baf:displayname>  
            </baf:designer>  
          </xs:appinfo>  
        </xs:annotation>  
      </xs:enumeration>  
      <xs:enumeration value="2">  
        <xs:annotation>  
          <xs:appinfo>  
            <baf:designer xmlns:baf="BiztalkAdapterFramework.xsd">  
              <baf:displayname _locID="createNewName">CreateNew</baf:displayname>  
            </baf:designer>  
          </xs:appinfo>  
        </xs:annotation>  
      </xs:enumeration>  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```