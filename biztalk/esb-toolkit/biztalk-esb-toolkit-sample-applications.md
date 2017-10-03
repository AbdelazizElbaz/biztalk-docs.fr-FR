---
title: Les Applications BizTalk ESB Toolkit exemple | Documents Microsoft
description: "Installer les exemples d’applications ESB Toolkit et obtenir des liens rapides sur la façon de les utiliser dans BizTalk Server"
caps.latest.revision: "5"
author: MandiOhlinger
manager: anneta
ms.custom: 
ms.date: 08/10/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 188f8e1f-26fb-4ea6-8e2e-f2ae3e46ca20
ms.author: mandia
ms.openlocfilehash: f9d1af5c2bc8c16ec14f8e13109f0edfe13b86cf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-esb-toolkit-sample-applications"></a>BizTalk ESB Toolkit exemple Applications
La [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] inclut plusieurs exemples d’applications que vous pouvez installer et exécuter pour voir comment des composants de pipeline de travaux ESB et comment il utilise certaines l’ESB. Vous pouvez adapter et modifier le code et les techniques utilisées dans les exemples pour vos propres applications.  
  
## <a name="install-the-sample-applications"></a>Installer les exemples d’applications  
  
1.  Créez un dossier nommé projets à la racine de votre lecteur C: et créez un sous-dossier nommé Microsoft.Practices.ESB dans ce dossier.  
  
    > [!NOTE]
    >  Dans la version actuelle, l’installation de prise en charge est pour les fichiers se trouvent dans le dossier C:\Projects\Microsoft.Practices.ESB. Les fichiers de liaison BizTalk qui sont fournis avec les exemples dépendent de ce chemin d’accès.  
  
2.  Lorsque vous installez le [ESB Toolkit](install-and-configure-the-microsoft-biztalk-esb-toolkit.md), il inclut un fichier .zip appelé ESBSource.zip dans l’emplacement d’installation que vous avez spécifié (par défaut, C:\Program Files\\[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]). Décompressez le fichier ESBSource.zip dans le dossier C:\Projects\Microsoft.Practices.ESB. Cela crée des dossiers nommés **clés** et **Source** qui contiennent l’exemple de clé et les exemples de code source. Le dossier Source contient le code source pour l’exemple d’application, et le dossier des clés contient les clés publiques utilisées pour signer les assemblys dans les exemples d’applications.  
  
3.  Avant d’exécuter les exemples, supprimez l’attribut en lecture seule sur le dossier C:\Projects\Microsoft.Practices.ESB\ afin que les exemples sont installés correctement.  
  
4.  Si vous n’avez pas utilisé avant de scripts PowerShell, vous devez ouvrir PowerShell en tant qu’administrateur et exécutez la commande suivante :  
  
    ```  
    set-executionpolicy unrestricted  
    ```  
  
    > [!NOTE]
    >  Pour plus d’informations sur PowerShell, consultez le [Blog Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=187593) ([http://go.microsoft.com/fwlink/? LinkId = 187593](http://go.microsoft.com/fwlink/?LinkId=187593)) et [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=187594) ([http://go.microsoft.com/fwlink/? LinkId = 187594](http://go.microsoft.com/fwlink/?LinkId=187594)) sur MSDN.  
  
5.  Ouvrez une invite de commandes en tant qu’administrateur et exécutez la commande suivante pour vérifier les scriptmaps WCF sont enregistrés :  
  
    ```  
    C:\Windows\Microsoft.NET\Framework\v3.0\Windows Communication Foundation>ServiceModelReg.exe -r -y  
    ```  
  
> [!NOTE]
>  Vous devez ouvrir le fichier ESBSource.zip afin d’obtenir un accès à du code des exemples.  

## <a name="sample-applications"></a>Exemples d’applications  
 Les rubriques suivantes décrivent les exemples d’applications et incluent des instructions d’installation supplémentaires, le cas échéant :  
  
-   [Installation des exemples de gestion des exceptions](../esb-toolkit/installing-the-exception-management-samples.md)  
  
-   [L’exemple de gestionnaire d’exceptions personnalisée réparation et soumettez à nouveau en cours d’exécution](../esb-toolkit/running-the-repair-and-resubmit-custom-exception-handler-sample.md)  
  
-   [Le Message de persistance d’exemple de gestionnaire d’exceptions personnalisé en cours d’exécution](../esb-toolkit/running-the-message-persisting-custom-exception-handler-sample.md)  
  
-   [Échec de l’exemple de traitement ESB du routage de Message BizTalk en cours d’exécution](../esb-toolkit/running-the-biztalk-failed-message-routing-esb-processing-sample.md)  
  
-   [Installer et exécuter l’exemple de rampe d’entrée d’itinéraire](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)  
  
-   [Installer et exécuter l’exemple de composant MQRFH2 JMS](../esb-toolkit/installing-and-running-the-jms-mqrfh2-component-sample.md)  
  
-   [Installer et exécuter l’exemple de composant de Namespace](../esb-toolkit/installing-and-running-the-namespace-component-sample.md)  
  
-   [Installer et exécuter l’exemple de Service de Transformation](../esb-toolkit/installing-and-running-the-transformation-service-sample.md)  
  
-   [Installer et exécuter l’exemple de résolution dynamique](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)  
  
-   [Installer et exécuter l’exemple d’opérations BizTalk](../esb-toolkit/installing-and-running-the-biztalk-operations-sample.md)  
  
-   [Installer et exécuter l’exemple de Service de programme de résolution](../esb-toolkit/installing-and-running-the-resolver-service-sample.md)  
  
-   [Installer et exécuter l’exemple de ventilation-regroupement](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md)  
  
-   [Installer et exécuter l’exemple d’enrichissement de Message](../esb-toolkit/installing-and-running-the-message-enrichment-sample.md)  
  
-   [Installer et exécuter l’exemple de Services Web multiples](../esb-toolkit/installing-and-running-the-multiple-web-services-sample.md)  
  
-   [Installer et exécuter l’exemple de l’extensibilité du Concepteur](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md)  
  
-   [Exemple de Service de gestion des exceptions en cours d’exécution](../esb-toolkit/running-the-exception-handling-service-sample.md)