---
title: "Énumérer les emplacements (exemple BizTalk Server) de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, examples
- receive locations, enumerating
- examples, receive locations
ms.assetid: 27ff8ac6-7e8e-4dde-84d1-d21bf417ddd7
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 82fcdc400395d7bbfd6de8f9bc0fca85114a25dc
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="enumerate-receive-locations-biztalk-server-sample"></a>Énumérer les emplacements (exemple BizTalk Server) de réception
L'exemple d'énumération des emplacements de réception décrit la récupération d'informations détaillées sur un ou plusieurs emplacements de réception.  
  
> [!WARNING]
>  Les scripts de déploiement devenus inutiles après le déploiement doivent être supprimés. Les scripts d'administration et autres scripts conservés doivent être sécurisés à l'aide de listes de contrôle d'accès et étroitement surveillés.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple inclut une version de Visual Basic Scripting Edition (VBScript) qui accède au modèle objet WMI Windows et une version Visual c# qui accède à la **System.Management** objets fournis par le .NET Framework. En dernier lieu, ces deux versions accèdent au fournisseur WMI de BizTalk Server pour effectuer les opérations suivantes :  
  
-   requête pour obtenir le jeu d'emplacements de réception configurés ou un emplacement de réception particulier, d'après son nom ;  
  
-   récupération et affichage des détails concernant chaque emplacement de réception qui vous intéresse ;  
  
-   gestion de toutes erreurs de telle sorte que les informations significatives soient renvoyées à l'utilisateur.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 Les exemples se trouvent dans les emplacements du Kit de développement logiciel (SDK) suivants :  
  
-   Version VBScript : \< *exemples de chemin*\>\Admin\WMI\Enumerate Receive Locations\VBScript\  
  
-   Version Visual c# : \< *exemples de chemin*\>\Admin\WMI\Enumerate Receive Locations\CSharp\  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|Dans le dossier \VBScript :<br /><br /> EnumRecLocs.vbs|Fichier VBScript qui récupère les détails concernant tous les emplacements de réception configurés.|  
|Dans le dossier \CSharp :<br /><br /> App.ico, AssemblyInfo.cs, BTSampleEnumerateRLs.csproj, BTSampleEnumerateRLs.sln, EnumRLs.cs|Fichiers de projet, de solution et sources pour la création d'une application de ligne de commande Visual C# qui récupère les détails sur tous les emplacements de réception configurés ou sur un emplacement de réception particulier.|  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
 La version VBScript de l'exemple d'énumération des emplacements de réception comporte un seul fichier de script Visual Basic, que vous ne devez ni installer ni initialiser.  
  
#### <a name="to-build-the-visual-c-version-of-the-enumerate-receive-locations-sample"></a>Pour créer la version Visual C# de l'exemple d'énumération des emplacements de réception  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le fichier de solution BTSampleEnumerateRLs.sln.  
  
2.  Dans le **générer** menu, cliquez sur **générer la Solution**.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
  
#### <a name="to-run-the-enumerate-receive-locations-sample"></a>Pour exécuter l'exemple d'énumération des emplacements de réception  
  
1.  Dans une fenêtre de commandes, accédez à l'un des dossiers suivants, selon que vous ayez choisi d'exécuter la version VBScript ou Visual C# de cet exemple, respectivement :  
  
     \<*Exemples de chemin d’accès*\>\Admin\WMI\Enumerate Locations\VBScript\ de réception  
  
     \<*Exemples de chemin d’accès*\>\Admin\WMI\Enumerate Locations\CSharp\bin\Debug\ de réception  
  
2.  En fonction de votre choix pour l'exécution de cet exemple (à savoir soit la version VBScript soit la version Visual C#), exécutez respectivement le fichier EnumRecLocs.vbs à l'aide du programme cscript ou le fichier EnumRl.exe. Pour la version Visual C#, exécutez l'un des deux arguments de ligne de commande suivants :  
  
    -   **\<ReceiveLocationName\>.** Correspond au nom de l'emplacement de réception pour lequel les détails seront affichés. Si le nom de l'emplacement de réception contient des espaces, placez-le entre guillemets.  
  
    -   **/?.** Affiche l’aide.  
  
         Par exemple (VBScript) :  
  
        ```  
        cscript EnumRecLocs.vbs  
        ```  
  
         - OU - (version Visual C#) :  
  
        ```  
        EnumRl "My Receive Location #3"  
        ```  
  
         - OU - (version Visual C#) :  
  
        ```  
        EnumRl /?  
        ```  
  
    > [!NOTE]
    >  La version VBScript de cet exemple n'accepte aucun paramètre de ligne de commande ; elle est donc uniquement capable de récupérer et d'afficher les détails concernant tous les emplacements de réception.  
  
## <a name="comments"></a>Commentaires  
 Toutes les tâches que vous pouvez effectuer dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration peut également être effectuée à l’aide de script qui accède au modèle objet WMI Windows et à l’aide de Visual c# qui accède à la **System.Management** objets fournis par le .NET Framework.  
  
 Le fichier de script EnumRecLocs.vbs et le fichier source Visual C# EnumRLs.cs contiennent des commentaires détaillés avec des explications plus précises sur les opérations qu'ils exécutent. Pour plus d’informations, consultez Windows Management Instrumentation à [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).  
  
## <a name="see-also"></a>Voir aussi  
 [Admin-WMI (dossier d’exemples BizTalk Server)](../core/admin-wmi-biztalk-server-samples-folder.md)