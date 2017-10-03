---
title: "Inscrire l’Orchestration (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- orchestrations, enlisting
- examples, orchestrations
ms.assetid: d8d53e59-2313-40dd-a278-0a29d8eb4ce8
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 95b03da5bf56367e59142a241dada6454a74c459
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="enlist-orchestration-biztalk-server-sample"></a>Inscrire l’Orchestration (exemple BizTalk Server)
L'exemple d'inscription de l'orchestration décrit l'inscription d'une orchestration BizTalk Server dans un hôte.  
  
> [!WARNING]
>  Les scripts de déploiement devenus inutiles après le déploiement doivent être supprimés. Les scripts d'administration et autres scripts conservés doivent être sécurisés à l'aide de listes de contrôle d'accès et étroitement surveillés.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple inclut une version de Visual Basic Scripting Edition (VBScript) qui accède au modèle objet Windows Management Instrumentation (WMI) et une version Visual c# qui accède à la **System.Management** fournis par des objets le .NET Framework. En dernier lieu, ces deux versions accèdent au fournisseur WMI de BizTalk Server pour effectuer les opérations suivantes :  
  
-   pour un nom d'orchestration et un nom d'assembly, création d'une requête pour une orchestration BizTalk Server déployée spécifique ;  
  
-   inscription de l'orchestration dans l'hôte par défaut ;  
  
-   gestion de toutes erreurs de telle sorte que les informations significatives soient renvoyées à l'utilisateur.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 Les exemples se trouvent dans les emplacements du Kit de développement logiciel (SDK) suivants :  
  
-   Version VBScript : \< *exemples de chemin*> \Admin\WMI\Enlist Orchestration\VBScript\  
  
-   Version Visual c# : \< *exemples de chemin*> \Admin\WMI\Enlist Orchestration\CSharp\  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|Dans le dossier \VBScript :<br /><br /> EnlistOrch.vbs|Fichier VBScript qui utilise des paramètres pour spécifier une orchestration à inscrire dans un hôte.|  
|Dans le dossier \CSharp :<br /><br /> App.ico, AssemblyInfo.cs, BTSampleEnlistOrc.csproj, BTSampleEnlistOrc.sln, EnlistOrc.cs|Fichiers de projet, de solution et sources pour la création d'une application de ligne de commande Visual C# qui utilise des paramètres pour spécifier une orchestration à inscrire dans un hôte.|  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
 La version VBScript de l'exemple d'inscription de l'orchestration comporte un seul fichier de script Visual Basic, que vous ne devez ni installer ni initialiser.  
  
#### <a name="to-build-the-visual-c-version-of-the-enlist-orchestration-sample"></a>Pour créer la version Visual C# de l'exemple d'inscription de l'orchestration  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le fichier de solution BTSampleEnlistOrc.sln.  
  
2.  Dans le **générer** menu, cliquez sur **générer la Solution**.  
  
#### <a name="to-run-the-enlist-orchestration-sample"></a>Pour exécuter l'exemple d'inscription de l'orchestration  
  
1.  Dans une fenêtre de commandes, accédez à l'un des dossiers suivants, selon que vous envisagiez d'exécuter la version VBScript ou Visual C# de cet exemple, respectivement :  
  
     \<*Exemples de chemin d’accès*> \Admin\WMI\Enlist Orchestration\VBScript\  
  
     \<*Exemples de chemin d’accès*> AdminWMIEnlist OrchestrationCSharpbinDebug  
  
2.  En fonction de votre choix pour l'exécution de cet exemple (à savoir soit la version VBScript soit la version Visual C#), exécutez respectivement le fichier EnlistOrch.vbs à l'aide du programme cscript ou le fichier EnlistOrc.exe. Dans les deux cas, exécutez les arguments de ligne de commande suivants :  
  
    -   **\<**   
         ***OrchestrationName* >.** Nom de l'orchestration à inscrire.  
  
    -   **\<**   
         ***AssemblyName* >.** Nom de l'assembly dans lequel l'orchestration a été déployée. Si le nom de l'assembly contient des espaces, placez-le entre guillemets.  
  
         Par exemple : (VBScript) :  
  
        ```  
        cscript EnlistOrch.vbs MyBusinessOrchestration "My Business Assembly"  
        ```  
  
         - OU - (version Visual C#) :  
  
        ```  
        EnlistOrc MyBusinessOrchestration "My Business Assembly"  
        ```  
  
## <a name="comments"></a>Commentaires  
 Toutes les tâches que vous pouvez effectuer dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration peut également être effectuée à l’aide de script qui accède au modèle objet WMI Windows et à l’aide de Visual c# qui accède à la **System.Management** objets fournis par le .NET Framework.  
  
 Le fichier de script EnlistOrch.vbs et le fichier source Visual C# EnlistOrc.cs contiennent des commentaires détaillés avec des explications plus précises sur les opérations qu'ils exécutent. Pour plus d’informations, consultez Windows Management Instrumentation à [http://go.microsoft.com/fwlink/?LinkId=21102](http://go.microsoft.com/fwlink/?LinkId=21102).  
  
## <a name="see-also"></a>Voir aussi  
 [Admin-WMI (dossier d’exemples BizTalk Server)](../core/admin-wmi-biztalk-server-samples-folder.md)