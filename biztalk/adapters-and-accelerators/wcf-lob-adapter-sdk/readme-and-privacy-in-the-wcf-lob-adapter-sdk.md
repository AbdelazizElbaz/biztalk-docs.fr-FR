---
title: "Fichier Lisezmoi et la confidentialité dans WCF LOB Adapter SDK | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 539a88f9-ce59-46e6-8c9a-418484eabff4
caps.latest.revision: "29"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b0e66bb7f13fd0a7cc39e983ac891708183662b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="readme-and-privacy-in-the-wcf-lob-adapter-sdk"></a>Fichier Lisezmoi et la confidentialité dans WCF LOB Adapter SDK
Le Windows Communication Foundation (WCF) Line de métier (LOB) adaptateur Kit de développement (SDK)  
  
## <a name="inside-the-sdk"></a>Dans le Kit de développement  
 Le tableau suivant présente le contenu des différents composants de WCF LOB Adapter SDK dans le \<dossier d’Installation\> après l’installation.  
  
|Type|Emplacement| Description|  
|----------|--------------|-----------------|  
|Durée d’exécution|\<Dossier d’installation\> \Bin\Microsoft.ServiceModel.Channels.dll<br /><br /> \<Dossier d’installation\> \Bin\Microsoft.ServiceModel.Channels.Tools.MetadataSearchBrowse.dll|Ces assemblys contiennent la base de temps, y compris le composant de formulaire principal utilisé dans les outils d’exécution.|  
|Outils|\<Dossier d’installation\> \Tools\Microsoft.ServiceModel.Channels.Tools.PlugInPackage.dll<br /><br /> \<Dossier d’installation\> \Tools\Microsoft.ServiceModel.Channels.Tools.BizTalkExtension.dll<br /><br /> \<Dossier d’installation\> \Tools\Microsoft.ServiceModel.Channels.Wizards.dll|**Ajouter l’adaptateur Service Reference Visual Studio plug-in**<br /><br /> (Projet .NET [droit], ajouter une référence de Service de l’adaptateur)<br /><br /> **Consume Adapter Service BizTalk Project Add-In**<br /><br /> (Projet BizTalk [droit], ajouter, ajouter les éléments générés, Consume Adapter Service)<br /><br /> **Assistant développement d’adaptateurs WCF LOB**<br /><br /> (Fichier, nouveau, projet, Visual c#, l’adaptateur WCF LOB)|  
|Documentation|\<Dossier d’installation\> \Documents\WCFLOBAdapterSDK.chm|Ce fichier contient le contenu conceptuel et le contenu de référence managée pour cette version.|  
|Fichier d’identificateur de produit|\<Dossier d’installation\>\Documents\pid.txt|Ce fichier contient l’identificateur de produit de WCF LOB Adapter SDK. Utilisez cet identificateur de produit comme référence lorsque vous contactez le Support technique et Service clientèle Microsoft.|  
|Exemples|\<Dossier d’installation\> \Documents\Samples\ContosoAdapterSample.zip<br /><br /> \<Dossier d’installation\> \Documents\Samples\EchoAdapterSample.zip|Le dossier d’exemples contient deux cartes exemple : Contoso adaptateur et adaptateur d’écho.|  

## <a name="privacy"></a>Confidentialité
Microsoft s’engage à protéger la confidentialité des utilisateurs finaux. Lorsque vous générez un adaptateur à l’aide de [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], il peut affecter la confidentialité de vos utilisateurs finals. Par exemple, votre adaptateur peut explicitement collecter et envoyer des informations d’identification de l’utilisateur, ou il peut envoyer et recevoir des informations sensibles à partir d’un système line-of-business. Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] n’envoie pas d’informations à Microsoft à partir de votre application, sauf si vous ou l’utilisateur choisit de nous l’envoyer.  
  
### <a name="windows-communication-foundation-privacy"></a>Confidentialité de Windows Communication Foundation  
 Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] est une extension de la [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] et par conséquent s’appuie sur de nombreux services fournis. Pour plus d’informations sur [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] confidentialité, consultez [informations de confidentialité de Windows Communication Foundation](https://msdn.microsoft.com/library/ms733927.aspx).  
  
### <a name="microsoft-wcf-lob-adapter-sdk-privacy"></a>Confidentialité de kit de développement logiciel Microsoft WCF LOB adaptateur  
 Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] est une API. En tant que développeur, vous pouvez fournir la journalisation personnalisée et le suivi des fonctionnalités pour faciliter le débogage, paramétrage, et l’audit dans les cartes que vous créez. Si vous ne fournissez pas ces fonctionnalités, vous devez prendre en compte le type d’informations que vous allez enregistrer et comment informations sera limitées afin que seules les personnes ont accès. Cela peut impliquer les éléments suivants :  
  
-   Définition et la gestion appropriée contrôle d’accès (ACL) sur les fichiers journaux et de la trace.  
  
-   Le filtrage des données sensibles avant de les écrire dans un fichier.  
  
-   Chiffrement des données sensibles avant de les écrire dans un fichier.  