---
title: "Gérer (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, examples
- utilities, SSOMANAGE
- examples, SSO
- SSOMANAGE command line utility
ms.assetid: f738e344-4d81-4557-b399-68b59c413245
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b15a94bf916550d9a2eada9b8f354432b4c154ff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manage-biztalk-server-sample"></a>Gérer (exemple BizTalk Server)
L'exemple de gestion de l'authentification unique (Manage Single Sign-On) illustre la génération de fichiers .xml que vous pouvez utiliser avec l'utilitaire de ligne de commande ssomanage.exe pour effectuer les types d'opérations d'administration suivants :  
  
-   mise à jour des informations globales au niveau du système d'authentification unique ;  
  
-   création d'applications associées ;  
  
-   création de mappages utilisateur.  
  
 Pour obtenir des informations conceptuelles sur Enterprise Single Sign-On, consultez [à l’aide de l’authentification unique](../core/using-sso.md).  
  
 Pour voir un exemple qui montre comment configurer par programme l’authentification unique, telles que la création d’applications associées et des mappages utilisateur, [HTTPSSO (exemple BizTalk Server)](../core/httpsso-biztalk-server-sample.md).  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple inclut des paires de fichiers XSD et fichiers .xml d'exemple pour chacun des types d'opérations mentionnés plus haut. Les valeurs des fichiers .xml d'exemple ne sont pas valides. Vous devez les modifier sur des valeurs adaptées à vos besoins spécifiques.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 *\<Exemples de chemin d’accès >*\SSO\Manage\  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|AffiliateApplication.xml, GlobalInfo.xml, UserMapping.xml|Fichiers .xml d'exemple que vous pouvez, après modification, transmettre sous forme d'arguments à l'utilitaire de ligne de commande ssomanage.exe.|  
|AffiliateApplication.xsd, GlobalInfo.xsd, UserMapping.xsd|Fichiers de schéma pour les fichiers .xml correspondants, qui fournissent une description complète de leurs éléments et attributs possibles. Vous pouvez utiliser ces fichiers pour valider les fichiers .xml correspondants reçus d'autres sources.|  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
 Comme cet exemple est constitué de fichiers XSD (XML Schema definition language) et de fichiers .xml uniquement, ces derniers pouvant être modifiés avant d'être transmis à l'utilitaire de ligne de commande ssomanage.exe, il n'y a pas d'étape de création dans cet exemple.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
 Cet exemple inclut des fichiers .xml d'exemple pour l'exécution de l'utilitaire de ligne de commande ssomanage.exe dans les trois modes suivants :  
  
-   **Mettre à jour des informations globales au niveau du système d’authentification unique.** . Pour effectuer ce type d'opération, procédez comme suit :  
  
    1.  Vous devez modifier le fichier GlobalInfo.xml en utilisant des valeurs adaptées à votre configuration spécifique.  
  
    2.  Exécutez l'utilitaire de ligne de commande ssomanage.exe à l'aide des arguments appropriés, comme suit :  
  
        ```  
        ssomanage –updatedb GlobalInfo.xml  
        ```  
  
     Veillez à modifier les valeurs du fichier GlobalInfo.xml sur des valeurs adaptées à votre environnement. Par exemple, le compte d'administrateur de l'authentification unique doit être un compte Windows valide. Le compte d'administrateur de l'authentification unique et le compte d'administrateur d'applications associées à authentification unique doivent être des comptes de groupe global de domaine Windows.  
  
-   **Création d’applications associées.** . Pour effectuer ce type d'opération, procédez comme suit :  
  
-   Modifiez le fichier AffiliateApplication.xml en utilisant des valeurs adaptées à votre configuration spécifique.  
  
    -   Exécutez l’utilitaire de ligne de commande ssomanage.exe avec les arguments appropriés, comme suit :  
  
        ```  
        ssomanage –createapps AffiliateApplication.xml  
        ```  
  
     Vous pouvez créer plusieurs applications associées simultanément.  
  
-   **Créer des mappages utilisateur.** . Pour effectuer ce type d'opération, procédez comme suit :  
  
    1.  Modifiez le fichier UserMapping.xml en utilisant des valeurs adaptées à votre configuration spécifique.  
  
    2.  Exécutez l’utilitaire de ligne de commande ssomanage.exe avec les arguments appropriés, comme suit :  
  
        ```  
        ssomanage –createmappings UserMapping.xml  
        ```  
  
     Vous pouvez créer plusieurs mappages pour une ou plusieurs applications associées simultanément.  
  
## <a name="comments"></a>Commentaires  
 Une fois les fichiers .xml fournis avec cet exemple modifiés, notamment lorsque les modifications impliquent l'intégration d'informations sensibles aux fichiers, assurez-vous que ces fichiers sont correctement protégés dans votre système de fichiers. Par exemple, vérifiez qu'ils ne sont pas placés par inadvertance dans un dossier partagé.  
  
## <a name="see-also"></a>Voir aussi  
 [Authentification unique (dossier d’exemples BizTalk Server)](../core/sso-biztalk-server-samples-folder.md)