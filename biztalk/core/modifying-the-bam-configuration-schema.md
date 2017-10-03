---
title: "La modification du schéma de Configuration BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration schema [BAM]
- managing [BAM], configuration schema
- BAMConfiguration.xml file
ms.assetid: 8901fb05-1519-4033-8489-67a9b745ed43
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87721445a19cff96799418c019560d09a1287488
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="modifying-the-bam-configuration-schema"></a><span data-ttu-id="ef2f2-102">Modification du schéma de configuration BAM</span><span class="sxs-lookup"><span data-stu-id="ef2f2-102">Modifying the BAM Configuration Schema</span></span>
<span data-ttu-id="ef2f2-103">L'Assistant Configuration crée ce fichier de configuration automatiquement.</span><span class="sxs-lookup"><span data-stu-id="ef2f2-103">The Configuration Wizard creates this configuration file automatically.</span></span> <span data-ttu-id="ef2f2-104">Vous devrez le modifier manuellement si vous changez vos noms de serveur ou d'autres informations de configuration une fois le déploiement terminé.</span><span class="sxs-lookup"><span data-stu-id="ef2f2-104">You must modify this file manually if you change your server names or other configuration information after you complete the deployment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef2f2-105">Pour activer les modifications qu'ils apportent au fichier de configuration BAM, les administrateurs doivent d'abord annuler le déploiement de la configuration BAM actuelle avant de déployer le fichier BAMConfiguration.xml mis à jour.</span><span class="sxs-lookup"><span data-stu-id="ef2f2-105">To enact the changes they make in the BAM configuration file, administrators must undeploy the current BAM configuration, and then deploy the updated BAMConfiguration.xml.</span></span>  
  
 <span data-ttu-id="ef2f2-106">Pour plus d’informations sur l’annulation du déploiement d’une définition BAM, consultez [des définitions BAM annulation du déploiement](../core/how-to-remove-bam-definitions.md).</span><span class="sxs-lookup"><span data-stu-id="ef2f2-106">For information about undeploying a BAM definition, see [Undeploying BAM Definitions](../core/how-to-remove-bam-definitions.md).</span></span> <span data-ttu-id="ef2f2-107">Pour plus d’informations sur le déploiement d’une définition BAM, consultez [déploiement de définitions BAM](../core/how-to-deploy-bam-definitions.md).</span><span class="sxs-lookup"><span data-stu-id="ef2f2-107">For information about deploying a BAM definition, see [Deploying BAM Definitions](../core/how-to-deploy-bam-definitions.md).</span></span>  
  
 <span data-ttu-id="ef2f2-108">Ce qui suit est le schéma utilisé pour le fichier BAMConfiguration.xml :</span><span class="sxs-lookup"><span data-stu-id="ef2f2-108">The following is the schema used for the BAMConfiguration.xml file:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-16" ?>  
<xs:schema xmlns="urn:schemas-microsoft.com:BAM" targetNamespace="urn:schemas-microsoft.com:BAM" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
     <xs:element name="BAMConfiguration">  
          <xs:complexType>  
               <xs:sequence>  
                    <xs:element name="DeploymentUnit" maxOccurs="unbounded" type="DeploymentUnit" />  
               </xs:sequence>  
          </xs:complexType>  
     </xs:element>  
     <xs:complexType name="DeploymentUnit">  
          <xs:sequence>  
               <xs:element name="Property" maxOccurs="unbounded" type="Property" />  
          </xs:sequence>  
          <xs:attribute name="Name" type="xs:string" />  
     </xs:complexType>  
     <xs:complexType name="Property">  
          <xs:simpleContent>  
               <xs:extension base='xs:string'>  
                    <xs:attribute name='Name' type='xs:NCName' />  
               </xs:extension>  
          </xs:simpleContent>  
     </xs:complexType>  
</xs:schema>  
```  
  
 <span data-ttu-id="ef2f2-109">Le fichier suivant est un exemple de fichier XML conforme au schéma de configuration BAM.</span><span class="sxs-lookup"><span data-stu-id="ef2f2-109">The following example is an XML file that conforms to the BAM configuration schema.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<BAM:BAMConfiguration xmlns:BAM='urn:schemas-microsoft.com:BAM' xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance'>  
     <DeploymentUnit Name="PrimaryImportDatabase">  
          <Property Name="ServerName">.</Property>  
          <Property Name="DatabaseName">BAMPrimaryImport</Property>  
          <Property Name="RTAWindow">60</Property>  
          <Property Name="RTATimeSlice">5</Property>  
     </DeploymentUnit>  
     <DeploymentUnit Name="StarSchemaDatabase">  
          <Property Name="ServerName">.</Property>  
          <Property Name="DatabaseName">BAMStarSchema</Property>  
     </DeploymentUnit>  
     <DeploymentUnit Name="AnalysisDatabase">  
          <Property Name="ServerName">localhost</Property>  
          <Property Name="DatabaseName">BAMAnalysis</Property>  
     </DeploymentUnit>  
     <DeploymentUnit Name="ArchivingDatabase">  
          <Property Name="ServerName">.</Property>  
          <Property Name="DatabaseName">BAMArchiving</Property>  
     </DeploymentUnit>  
     <DeploymentUnit Name="CubeUpdateDTS">  
          <Property Name="ConnectionTimeOut">15</Property>  
          <Property Name="UseEncryption">1</Property>  
          <Property Name="OwnerPassword">myOwnerPassword</Property>  
          <Property Name="UserPassword">myUserPassword</Property>  
     </DeploymentUnit>  
     <DeploymentUnit Name="DataMaintenanceDTS">  
          <Property Name="ConnectionTimeOut">15</Property>  
          <Property Name="UseEncryption">1</Property>  
          <Property Name="OwnerPassword">myOwnerPassword</Property>  
          <Property Name="UserPassword">myUserPassword</Property>       
     </DeploymentUnit>  
</BAM:BAMConfiguration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ef2f2-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef2f2-110">See Also</span></span>  
 <span data-ttu-id="ef2f2-111">[Schéma de Configuration BAM](../core/bam-configuration-schema.md) </span><span class="sxs-lookup"><span data-stu-id="ef2f2-111">[BAM Configuration Schema](../core/bam-configuration-schema.md) </span></span>  
 <span data-ttu-id="ef2f2-112">[Recommandations de sécurité BAM](../core/bam-security-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="ef2f2-112">[BAM Security Recommendations](../core/bam-security-recommendations.md) </span></span>  
 [<span data-ttu-id="ef2f2-113">Business Activity Monitoring (BAM)</span><span class="sxs-lookup"><span data-stu-id="ef2f2-113">Business Activity Monitoring (BAM)</span></span>](../core/business-activity-monitoring-bam.md)