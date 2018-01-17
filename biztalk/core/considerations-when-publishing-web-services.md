---
title: "Considérations relatives à la publication de Services Web | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, publishing
- Web services, planning
- Web services, schemas
- schemas, Web services
ms.assetid: 3ace0260-a1cb-4e59-a820-36ee7d5cceda
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 825a16555f0b0c82282ae4d85592567d2a19c073
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="considerations-when-publishing-web-services"></a>Considérations à prendre en compte lors de la publication de services Web
Cette rubrique fournit des informations que vous devez prendre en compte avant de publier vos services Web.  
  
## <a name="publishing-schemas-and-the-include-element"></a>Publication de schémas et de l'élément include  
 Il existe quelques scénarios où les schémas qui contiennent le **incluent** élément ne peut pas être publié comme service Web. Une erreur se produira lorsque vous aurez terminé d'utiliser l'Assistant Publication de services Web BizTalk. Ces restrictions sont les suivantes :  
  
-   Circulaire inclut (le schéma inclus a un **incluent** élément vers le schéma, y compris)  
  
-   Un non résolue **schemaLocation** attribut provoque une erreur  
  
 Pour plus d’informations sur la limitation des élément include, consultez « Include Element Binding Support » à l’adresse [http://go.microsoft.com/fwlink/?LinkId=62312](http://go.microsoft.com/fwlink/?LinkId=62312).  
  
## <a name="publishing-schemas-and-the-import-element"></a>Publication de schémas et de l'élément import  
 L'Assistant Publication de services Web BizTalk a la même restriction que XSD.exe inclus dans .NET Framework. Pour plus d’informations, consultez « Import Element Binding Support » à [http://go.microsoft.com/fwlink/?LinkId=62311](http://go.microsoft.com/fwlink/?LinkId=62311).  
  
## <a name="publishing-schemas-and-the-redefine-element"></a>Publication de schémas et de l'élément redefine  
 L'Assistant Publication de services Web BizTalk a la même restriction que XSD.exe inclus dans .NET Framework. Pour plus d’informations, consultez « Redefine Element Binding Support » à [http://go.microsoft.com/fwlink/?LinkId=62313](http://go.microsoft.com/fwlink/?LinkId=62313).  
  
## <a name="publishing-schemas-that-specify-values-for-minoccurs-or-maxoccurs-attributes"></a>Publication de schémas qui spécifient les valeurs des attributs minOccurs ou maxOccurs  
 Si vous publiez un schéma qui contient **minOccurs** ou **maxOccurs** attributs avec des valeurs spécifiques, ces valeurs peuvent être différentes dans le schéma exposé par le service Web publié. En guise de point de repère général, tous les attributs minOccurs sont convertis en 0 (minOccurs=0) et les attributs maxOccurs sont convertis en 1 ou unbounded (maxOccurs=1 ou maxOccurs=unbounded).  
  
## <a name="publishing-envelope-schemas"></a>Publication de schémas d'enveloppe  
 Si vous avez un schéma d'enveloppe que vous publiez en tant que service Web, vous devez modifier manuellement le projet Web généré.  
  
#### <a name="to-modify-the-generated-web-project-for-envelope-schemas"></a>Pour modifier le projet Web généré pour les schémas d'enveloppe  
  
1.  Ouvrez le fichier <`myWebService`>.asmx.cs.  
  
2.  Modifiez le fichier et remplacez `bodyTypeAssemblyQualifiedName = <dll.name.version.>` par `bodyTypeAssemblyQualifiedName = null`.  
  
> [!NOTE]
>  Vous devrez peut-être rétablir les services Internet (IIS) si le fichier .dll précédent est toujours dans le processus de travail ASPNET.  
  
## <a name="web-service-and-web-method-attributes"></a>Attributs du service Web et de la méthode Web  
 L'Assistant Publication de services Web BizTalk ne vous permet pas de personnaliser les attributs du service Web ou de la méthode Web que vous utilisez dans ASP.NET. Certains attributs sont automatiquement définis en fonction des informations fournies par l'Assistant. L'Assistant n'utilise pas les autres attributs.  
  
 La modification des attributs existants ou l'ajout de nouveaux attributs aux services Web générés par l'Assistant Publication de services Web BizTalk peut entraîner le dysfonctionnement du service Web.  
  
 Pour plus d’informations sur les services Web et les attributs de méthode Web, consultez le **WebServiceAttribute** et **WebMethodAttribute** classes dans la documentation du Kit de développement logiciel .NET Framework.  
  
## <a name="web-method-required"></a>Méthode Web requise  
 Un service Web doit avoir au moins une méthode Web. Sans au moins une méthode Web, les types de ports n'auront pas leurs opérations créées. XLANG/s ne prend pas en charge les types de ports qui n'ont pas d'opérations.  
  
## <a name="dbcs-character-support"></a>Prise en charge des caractères DBCS  
 Les services Web ne prennent pas en charge les idéographes unifiés CJC (chinois/japonais/coréens) - extension A.  
  
## <a name="republishing-web-services-using-the-biztalk-web-services-publishing-wizard"></a>Republication de services Web à l'aide de l'Assistant Publication de services Web BizTalk  
 Vous pouvez utiliser l'Assistant Publication de services Web BizTalk pour republier un service Web publié. Sur le **Web *** Service *** projet** page, vous pouvez sélectionner le **remplacer *** Web *** Service** option.  
  
 L'Assistant ne stocke pas les paramètres précédemment utilisés. Si vous modifiez les paramètres lors de la nouvelle exécution de l'Assistant, tout client Web qui utilise (appelle) le service Web publié risque d'échouer. Vous devez mettre à jour les références Web des clients qui utilisent (appellent) un service Web republié.  
  
## <a name="clients-of-published-web-services-may-not-receive-server-script-timeout-errors"></a>Les clients de services Web publiés risquent de ne pas recevoir des erreurs de délai d'expiration de script du serveur.  
 Services Web générés avec l’Assistant Publication de Services Web dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont configurés par défaut avec une valeur de délai d’expiration de script de **110** secondes. Il s'agit de la valeur par défaut pour la propriété **HttpServerUtility.ScriptTimeout** propriété. Les clients Web qui utilisent .NET Framework sont configurés par défaut avec une valeur de délai d’attente de demande de **100** secondes. C’est la valeur par défaut pour le .NET Framework **HttpWebRequest.Timeout** propriété.  
  
 Si les clients Web qui utilisent .NET Framework appellent un service Web généré avec l'Assistant Publication de services Web [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], il se peut que le client ne puisse pas recevoir d'erreurs de délai d'expiration de script du serveur car le délai d'expiration de la requête du client a lieu en premier, par défaut. Pour résoudre ce problème, vous pouvez effectuer une des opérations suivantes :  
  
-   Augmenter le délai d’attente de demande client pour une valeur supérieure au délai d’expiration de script de serveur en augmentant la valeur de la **HttpWebRequest.Timeout** propriété sur le client.  
  
-   Réduire le délai d’expiration de script de serveur à une valeur inférieure au délai de demande client en réduisant la valeur pour le **HttpServerUtility.ScriptTimeout** propriété sur le serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication de services web](../core/publishing-web-services.md)