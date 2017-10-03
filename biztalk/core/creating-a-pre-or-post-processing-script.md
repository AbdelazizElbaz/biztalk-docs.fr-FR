---
title: "Création d’une commande avant ou le Script de post-traitement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scripts, post-processing
- scripts, pre-processing
- scripts, warnings
- scripts, applications
- applications, scripts
- scripts, deploying
- deploying, scripts
ms.assetid: d5fbaec8-fbfe-4ceb-8ba8-0933baa37a1f
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 532c730d5a654512610a37c9dac783fbc6a76d6c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-pre--or-post-processing-script"></a>Création d'un script de pré-traitement ou de post-traitement
Vous pouvez créer un script qui effectue des opérations lors du déploiement d'une application, puis définir le moment où ce script doit être exécuté durant le processus. Vous pouvez insérer le code d'installation et le code de nettoyage dans le même script en vous servant des variables d'environnement pour délimiter le code. Il est également possible de passer des arguments en ligne de commande au script.  
  
> [!CAUTION]
>  Écrivez toujours les scripts destinés à des systèmes de production en mode silencieux. En effet, lorsque le script est en attente de données, les bases de données BizTalk se verrouillent et ne sont plus accessibles tant que l'utilisateur n'a pas entré les données requises.  
  
## <a name="specifying-when-a-script-will-run-during-deployment"></a>Spécification du moment d'exécution d'un script lors du déploiement  
 Vous indiquez le moment où le script doit être exécuté lorsque vous ajoutez le script à une application, soit en tant que System.BizTalk:PreProcessingScript (script de pré-traitement), soit en tant que System.BizTalk:PostProcessingScript (script de post-traitement).  
  
 Les scripts de pré-traitement et de post-traitement s'exécutent comme suit :  
  
-   Les scripts de pré-traitement s'exécutent au début du processus d'importation ou d'installation.  
  
-   Les scripts de post-traitement s'exécutent à la fin du processus d'importation ou d'installation.  
  
-   Lors d'une désinstallation, tous les scripts s'exécutent dans l'ordre inverse à celui dans lequel ils s'exécutent lors d'une installation. Par conséquent, les scripts de post-traitement s'exécutent au début du processus de désinstallation et les scripts de pré-traitement, à la fin.  
  
-   Si une installation échoue, les scripts sont appelés dans l'ordre inverse, en suivant l'action d'annulation appropriée.  
  
 Une fois appelé, un script de pré-traitement ou post-traitement détermine quel état de déploiement (installer, importer, supprimer, désinstaller, annulation de l’importation ou installer rollback) il s’exécute en vérifiant les variables d’environnement BTAD_ChangeRequestAction, BTAD_InstallMode, et BTAD_HostClass, comme décrit dans [état du déploiement de l’environnement Variables indiquer](../core/how-environment-variables-indicate-deployment-state.md). Pour plus d’informations de référence sur les variables, consultez [Variables d’environnement de Script et de post-traitement](../core/pre-and-post-processing-script-environment-variables.md).  
  
 Pour obtenir des instructions sur l’ajout d’un script à une application, consultez [Ajout antérieur à la version ou un Script de post-traitement à une Application](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md).  
  
> [!NOTE]
>  Si vous souhaitez insérer des arguments en ligne de commande à un script, comme mentionné plus loin dans cette rubrique, vous devez utiliser la commande AddResource lorsque vous ajoutez le script.  
  
## <a name="supported-script-file-extensions"></a>Extensions de fichier de script prises en charge  
 Les extensions de fichier de script suivantes sont prises en charge : .com, .exe, .bat, .cmd, .vbs, .vbe, .js, .jse, .wsf et .wsh. Cet ensemble d'extensions est défini dans la variable d'environnement PATHEXT.  
  
## <a name="logging-errors"></a>Consignation des erreurs  
 Il est recommandé de configurer chaque script de sorte qu'il consigne les erreurs dans un fichier. En effet, Windows Installer ne consigne pas les erreurs éventuellement générées dans les scripts. Une fois le script exécuté, vérifiez que les fichiers journaux ne contiennent pas d'erreurs nécessitant votre intervention.  
  
 Pour pouvoir déterminer plus facilement le moment où l'erreur s'est produite, vous pouvez inclure la date et l'heure dans le fichier journal.  
  
 Utilisez le code suivant pour spécifier un fichier journal et y consigner les erreurs.  
  
 `Set LogFile=<full path of log file>`  
  
 `…`  
  
 `echo %DATE% %TIME% <text> >> %LogFile%`  
  
 Dans l'exemple suivant, une entrée est créée dans le fichier journal spécifié lorsque le jeton de clé publique n'est pas défini. Dans ce fichier journal, la date et l'heure sont écrits sur la même ligne, comme indiqué dans la ligne de code « Public key should be set in script » ci-dessous.  
  
 `set LogFile=C:\ScriptLog.txt`  
  
 `set PublicKeyToken=e5fd0ea4ecd37420`  
  
 `if not defined PublicKeyToken (`  
  
 `echo %DATE% %TIME% Public key should be set in script >> %LogFile%`  
  
 Vous pouvez ajouter la ligne `exit /b 1` à un script afin qu'un code d'erreur soit généré pour Windows Installer. Cet ajout entraîne l'annulation de l'exécution de Windows Installer.   
  
 Dans l'exemple suivant, le script signale une erreur à Windows Installer si le jeton de clé publique n'a pas été défini.  
  
 `set LogFile=C:\ScriptLog.txt`  
  
 `set PublicKeyToken=e5fd0ea4ecd37420`  
  
 `if not defined PublicKeyToken (`  
  
 `echo %DATE% %TIME% Public key should be set in script >> %LogFile%`  
  
 `exit /b 1`  
  
## <a name="including-installation-and-cleanup-code-in-the-same-script"></a>Insertion du code d'installation et du code de nettoyage dans le même script  
 Étant donné que les scripts s'exécutent dans l'ordre inverse selon qu'il s'agit d'une installation ou d'une désinstallation, vous pouvez inclure un code d'installation et un code de nettoyage dans le même script, dans une instruction conditionnelle. Par exemple, vous pouvez placer le code d'installation dans une instruction conditionnelle qui vérifie le mode d'installation comme suit :  
  
```  
  
%BTAD_ChangeRequestAction%=Update AND %BTAD_InstallMode%=Install  
  
```  
  
 Vous pouvez qualifier le code de nettoyage dans une instruction conditionnelle qui vérifie le mode d'installation comme suit :  
  
```  
  
%BTAD_ChangeRequestAction%=Delete AND %BTAD_InstallMode%=Uninstall  
  
```  
  
## <a name="passing-in-command-line-arguments"></a>Passage d'arguments en ligne de commande  
 Pour passer des arguments en ligne de commande au script, spécifiez le paramètre décrit ci-après lorsque vous ajoutez le script à l'application à l'aide de la commande BTSTask AddResource. Cela fait, les arguments sont passés au script lorsque ce dernier est invoqué.  
  
 **/Property:args =**»*liste d’arguments*»  
  
> [!NOTE]
>  Lorsque vous avez plusieurs scripts de pré-traitement et de post-traitement dans une application, ils sont exécutés sans respecter d'ordre particulier.  
  
> [!IMPORTANT]
>  N'utilisez pas de commandes BTSTask dans les scripts, surtout dans les scripts qui s'exécutent lors de l'importation car ces scripts ne sont pas inscrits dans la même transaction qu'une importation.  
  
 Pour obtenir des instructions sur l’utilisation de la commande AddResource pour ajouter un script à une application, consultez [commande AddResource : scripts de pré-traitement](../core/addresource-command-preprocessing-script.md). Consultez également [commande AddResource : scripts de post-traitement](../core/addresource-command-postprocessing-script.md)  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de Scripts de pré-traitement et post-traitement pour personnaliser le déploiement d’Application](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md)   
 [Modèle (exemple de déploiement d’Application)](../core/template-application-deployment-sample.md)