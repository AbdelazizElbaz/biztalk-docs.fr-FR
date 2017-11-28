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
ms.openlocfilehash: 2afa0e2f06471d90326b0dd8e2b83b8d4c38a82b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adapter-configuration-schemas"></a><span data-ttu-id="c97f6-102">Schémas de configuration de l'adaptateur</span><span class="sxs-lookup"><span data-stu-id="c97f6-102">Adapter Configuration Schemas</span></span>
<span data-ttu-id="c97f6-103">Différents types de schémas sont utilisés pour la configuration de la conception d'un adaptateur.</span><span class="sxs-lookup"><span data-stu-id="c97f6-103">Different types of schemas are used in design-time configuration of an adapter.</span></span> <span data-ttu-id="c97f6-104">En fonction de la visibilité et de l'étendue des valeurs de propriété, divers schémas sont modifiés et utilisés.</span><span class="sxs-lookup"><span data-stu-id="c97f6-104">Depending upon the visibility and scope of property values, different schemas are modified and used.</span></span>  
  
## <a name="handler-schemas"></a><span data-ttu-id="c97f6-105">Schémas de gestionnaire</span><span class="sxs-lookup"><span data-stu-id="c97f6-105">Handler Schemas</span></span>  
 <span data-ttu-id="c97f6-106">La configuration de l'adaptateur fournie par un gestionnaire s'applique à l'adaptateur et à tous ses consommateurs dans une étendue globale.</span><span class="sxs-lookup"><span data-stu-id="c97f6-106">Adapter configuration that comes from a handler applies to the adapter and all its consumers on a global scope.</span></span> <span data-ttu-id="c97f6-107">Un administrateur peut modifier de manière statique la configuration d'un gestionnaire au moment de la conception en utilisant la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour développer le gestionnaire de réception ou d'envoi de l'adaptateur et afficher les propriétés de l'hôte spécifié.</span><span class="sxs-lookup"><span data-stu-id="c97f6-107">An administrator can statically alter handler configuration at design time by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to expand the adapter's receive or send handler and bring up the properties of the specified host.</span></span>  
  
 <span data-ttu-id="c97f6-108">L'exemple de l'adaptateur File du kit de développement logiciel (SDK) comporte un ensemble de fichiers XSD utilisés pour configurer son emplacement de réception, son port d'envoi, son gestionnaire de réception et son gestionnaire d'envoi.</span><span class="sxs-lookup"><span data-stu-id="c97f6-108">The sample file adapter included in the SDK has a set of XSD files used to configure its receive location, send port, receive handler, and send handler.</span></span> <span data-ttu-id="c97f6-109">Modifiez ces fichiers XSD de sorte que votre adaptateur personnalisé reçoive les propriétés de configuration qu'il requiert.</span><span class="sxs-lookup"><span data-stu-id="c97f6-109">Modify these XSD files so that your custom adapter receives the configuration properties it requires.</span></span> <span data-ttu-id="c97f6-110">Les fichiers que vous devez modifier dans l'exemple d'adaptateur File sont les fichiers de schéma TransmitHandler.xsd et ReceiveHandler.xsd.</span><span class="sxs-lookup"><span data-stu-id="c97f6-110">The files included with the sample file adapter that you need to modify are the TransmitHandler.xsd and ReceiveHandler.xsd schema files.</span></span> <span data-ttu-id="c97f6-111">Ces fichiers configurent respectivement le gestionnaire d'envoi et le gestionnaire de réception, en contrôlant les pages de propriétés utilisées pour configurer les gestionnaires dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c97f6-111">These files configure the send handler and receive handler, respectively, by controlling the property pages used to configure the handlers in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
 <span data-ttu-id="c97f6-112">À l'aide de vos exigences d'adaptateur, créez une liste des propriétés de configuration requises pour chacun des points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="c97f6-112">Using your adapter requirements, create a list of configuration properties required for each of the endpoints.</span></span> <span data-ttu-id="c97f6-113">Si l'ensemble de ces propriétés sont globales, vous n'aurez sans doute qu'à modifier les configurations des ports d'envoi et des ports de réception.</span><span class="sxs-lookup"><span data-stu-id="c97f6-113">If all of your configuration properties are global, you may only need to modify the send and receive port configurations.</span></span> <span data-ttu-id="c97f6-114">Si les propriétés de l'adaptateur doivent être définies pour chaque port d'envoi ou emplacement de réception, il vous faudra également modifier les fichiers de configuration d'emplacement de réception et de port d'envoi. </span><span class="sxs-lookup"><span data-stu-id="c97f6-114">If the adapter properties need to be set for each send port or receive location, you have to modify the receive location and send port configuration files as well.</span></span>  
  
 <span data-ttu-id="c97f6-115">L'infrastructure d'adaptateurs fournit des extensions de schéma et des options avancées de configuration prenant en charge les conditions requises communes pour la configuration des adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="c97f6-115">The Adapter Framework provides schema extensions and advanced configuration options to support common adapter configuration requirements.</span></span> <span data-ttu-id="c97f6-116">Elle fournit de plus des extensions qui ne figurent pas dans le schéma inclus avec l'exemple d'adaptateur FILE.</span><span class="sxs-lookup"><span data-stu-id="c97f6-116">It also provides extensions that are not in the schema included with the sample file adapter.</span></span> <span data-ttu-id="c97f6-117">Pour plus d’informations sur les extensions de schéma d’infrastructure d’adaptateurs, consultez [Extensions de schéma de Configuration Framework adaptateur](../core/adapter-framework-configuration-schema-extensions.md).</span><span class="sxs-lookup"><span data-stu-id="c97f6-117">For more information about the Adapter Framework schema extensions, see [Adapter Framework Configuration Schema Extensions](../core/adapter-framework-configuration-schema-extensions.md).</span></span> <span data-ttu-id="c97f6-118">Pour plus d’informations sur les options de configuration avancées telles que les éditeurs déroulants personnalisés et les convertisseurs de type personnalisé, consultez [des composants de Configuration avancée pour les adaptateurs](../core/advanced-configuration-components-for-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="c97f6-118">For more information about advanced configuration options such as custom drop-down editors and custom type converters, see [Advanced Configuration Components for Adapters](../core/advanced-configuration-components-for-adapters.md).</span></span>  
  
 <span data-ttu-id="c97f6-119">Le code qui figure à la fin de cette rubrique est issu du fichier TransmitHandler.xsd. Il génère la page de propriétés suivante.</span><span class="sxs-lookup"><span data-stu-id="c97f6-119">The code at the end of this topic is from the TransmitHandler.xsd file, and produces the following property page.</span></span>  
  
 ![](../core/media/ebiz-prog-custad-sh.gif "ebiz_prog_custad_sh")  
<span data-ttu-id="c97f6-120">Page de propriétés du gestionnaire d'envoi, créée par le fichier TransmitHandler.xsd</span><span class="sxs-lookup"><span data-stu-id="c97f6-120">Send handler property page created by the TransmitHandler.xsd file</span></span>  
  
 <span data-ttu-id="c97f6-121">Notez l’utilisation de la \<baf : Designer >, \<baf : DisplayName >, et \<baf : description > balises dans le code TransmitHandler.xsd présenté ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="c97f6-121">Note the use of the \<baf:designer>, \<baf:displayname>, and \<baf:description> tags in the TransmitHandler.xsd code that is shown below.</span></span> <span data-ttu-id="c97f6-122">Il s'agit de décorations personnalisées fournies par l'infrastructure d'adaptateurs pour accélérer la génération des pages de propriétés.</span><span class="sxs-lookup"><span data-stu-id="c97f6-122">These are custom decorations provided by the Adapter Framework to make the generation of these property pages faster.</span></span>  
  
 <span data-ttu-id="c97f6-123">Pour obtenir la liste de toutes les décorations disponibles pour une utilisation dans l’infrastructure d’adaptateurs, consultez [balises d’ornement adaptateur Framework Configuration schéma](../core/adapter-framework-configuration-schema-decoration-tags.md).</span><span class="sxs-lookup"><span data-stu-id="c97f6-123">For a list of all of the decorations available for use within the Adapter Framework, see [Adapter Framework Configuration Schema Decoration Tags](../core/adapter-framework-configuration-schema-decoration-tags.md).</span></span>  
  
 <span data-ttu-id="c97f6-124">Notez que le schéma ne comporte qu'un élément et qu'il ne contient aucun élément URI.</span><span class="sxs-lookup"><span data-stu-id="c97f6-124">Note that the schema has only one element and does not contain a URI element.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c97f6-125">Ne stockez pas de données sensibles relatives aux clients dans le schéma d'adaptateur par défaut.</span><span class="sxs-lookup"><span data-stu-id="c97f6-125">Do not store sensitive customer data in the default adapter schema.</span></span> <span data-ttu-id="c97f6-126">Pour des raisons de sécurité, il est recommandé de configurer le nom d'utilisateur et le mot de passe uniquement après avoir déployé un adaptateur.</span><span class="sxs-lookup"><span data-stu-id="c97f6-126">For security reasons, configure user name and password information only after you deploy an adapter.</span></span> <span data-ttu-id="c97f6-127">Cela garantit que les informations sont bien stockées dans la base de données de l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="c97f6-127">This ensures that the information gets stored in the Enterprise Single Sign-On (SSO) database.</span></span> <span data-ttu-id="c97f6-128">Pour plus d’informations sur la base de données SSO, consultez [à l’aide de l’authentification unique](../core/using-sso.md).</span><span class="sxs-lookup"><span data-stu-id="c97f6-128">For more information about the SSO database, see [Using SSO](../core/using-sso.md).</span></span>  
  
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
  
## <a name="send-port-and-receive-location-schemas"></a><span data-ttu-id="c97f6-129">Schémas du port d'envoi et de l'emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="c97f6-129">Send Port and Receive Location Schemas</span></span>  
 <span data-ttu-id="c97f6-130">Pour définir des propriétés spécifiques aux ports de votre adaptateur, modifiez les schémas de configuration de l'emplacement de réception et du port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="c97f6-130">To set port-specific properties for your adapter, modify the receive location and send port configuration schemas.</span></span> <span data-ttu-id="c97f6-131">Les fichiers de schéma TransmitLocation.xsd et ReceiveLocation.xsd configurent le port d'envoi et l'emplacement de réception respectivement.</span><span class="sxs-lookup"><span data-stu-id="c97f6-131">The TransmitLocation.xsd and ReceiveLocation.xsd schema files configure the send port and receive location, respectively.</span></span>  
  
 <span data-ttu-id="c97f6-132">L'infrastructure d'adaptateurs fournit des extensions de schéma et des options avancées de configuration prenant en charge les conditions requises communes pour la configuration des adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="c97f6-132">The Adapter Framework provides schema extensions and advanced configuration options to support common adapter configuration requirements.</span></span> <span data-ttu-id="c97f6-133">Pour plus d’informations sur les extensions de schéma d’infrastructure d’adaptateurs, consultez [Extensions de schéma de Configuration Framework adaptateur](../core/adapter-framework-configuration-schema-extensions.md).</span><span class="sxs-lookup"><span data-stu-id="c97f6-133">For more information about the Adapter Framework schema extensions, see [Adapter Framework Configuration Schema Extensions](../core/adapter-framework-configuration-schema-extensions.md).</span></span> <span data-ttu-id="c97f6-134">Pour plus d’informations sur les options de configuration avancées telles que les éditeurs déroulants personnalisés et les convertisseurs de type personnalisé, consultez [des composants de Configuration avancée pour les adaptateurs](../core/advanced-configuration-components-for-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="c97f6-134">For more information about advanced configuration options such as custom drop-down editors and custom type converters, see [Advanced Configuration Components for Adapters](../core/advanced-configuration-components-for-adapters.md).</span></span>  
  
 <span data-ttu-id="c97f6-135">Le code qui suit est issu du fichier TransmitLocation.xsd. Il génère la page de propriétés suivante.</span><span class="sxs-lookup"><span data-stu-id="c97f6-135">The code that follows is from the TransmitLocation.xsd file, and produces the following property page.</span></span>  
  
 ![](../core/media/ebiz-prog-custad-sp.gif "ebiz_prog_custad_sp")  
<span data-ttu-id="c97f6-136">Illustration de la page de propriétés du port d'envoi de l'exemple d'adaptateur FILE.</span><span class="sxs-lookup"><span data-stu-id="c97f6-136">Illustrates the send port property page for the sample file adapter</span></span>  
  
 <span data-ttu-id="c97f6-137">Notez que, dans le fichier TransmitLocation.xsd ci-dessous que la configuration du port d’envoi contient le \<baf : Designer >, \<baf : DisplayName >, et \<baf : description > balises, tout comme le Gestionnaire d’envoi, il utilise également le \<baf : Category > balise.</span><span class="sxs-lookup"><span data-stu-id="c97f6-137">Note in the TransmitLocation.xsd file below that the send port configuration contains the \<baf:designer>, \<baf:displayname>, and \<baf:description> tags, just like the send handler, and it also uses the \<baf:category> tag.</span></span> <span data-ttu-id="c97f6-138">La balise « category » vous permet de regrouper les propriétés.</span><span class="sxs-lookup"><span data-stu-id="c97f6-138">The category tag enables you to group properties together.</span></span> <span data-ttu-id="c97f6-139">Si vous avez plus d'une catégorie, chacune peut être développée ou réduite et apparaît sous la forme d'un en-tête gris au-dessus des propriétés qui lui correspondent.</span><span class="sxs-lookup"><span data-stu-id="c97f6-139">If you have more than one category, the category is expandable and collapsible and appears in gray as a header above the properties in that category.</span></span> <span data-ttu-id="c97f6-140">Pour plus d’informations, consultez [Extensions de schéma de Configuration Framework adaptateur](../core/adapter-framework-configuration-schema-extensions.md).</span><span class="sxs-lookup"><span data-stu-id="c97f6-140">For more information, see [Adapter Framework Configuration Schema Extensions](../core/adapter-framework-configuration-schema-extensions.md).</span></span>  
  
 <span data-ttu-id="c97f6-141">Ce schéma contient également un champ URI.</span><span class="sxs-lookup"><span data-stu-id="c97f6-141">This schema also contains a URI field.</span></span> <span data-ttu-id="c97f6-142">Il est renseigné dans la page qui apparaît une fois que vous avez entré toutes les informations de champ dans la page des propriétés du port d'envoi au cours du traitement de validation effectué par l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="c97f6-142">This is populated on the page that appears after you enter all of the field information on the send port property page during the validation processing by the adapter.</span></span>  
  
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