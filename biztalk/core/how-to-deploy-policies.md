---
title: "Comment déployer des stratégies | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c4ab85a-5a6a-4153-90dc-52e099c0a62c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c3b07b0a8cebdd3322b49732ef4f32c04cbfede
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-deploy-policies"></a>Déploiement des stratégies
Vous pouvez déployer des stratégies par programmation à l’aide de la [Microsoft.RuleEngine.RuleSetDeploymentDriver](http://msdn.microsoft.com/library/microsoft.ruleengine.rulesetdeploymentdriver.aspx) classe dans le **Microsoft.RuleEngine.RuleEngineExtensions** espace de noms. L’exemple de code suivant montre comment utiliser le [Microsoft.RuleEngine.RuleSetDeploymentDriver](http://msdn.microsoft.com/library/microsoft.ruleengine.rulesetdeploymentdriver.aspx) classe pour déployer une stratégie nommée **LoanProcessing**:  
  
```  
string policyName = “LoanProcessing”;  
int majorRev = Convert.ToInt16(args[1]);  
int minorRev = Convert.ToInt16(args[2]);  
RuleSetInfo rsi = new RuleSetInfo(policyName,majorRev,minorRev);  
Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver dd;  
dd = new Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver();  
dd.Deploy(rsi);  
```  
  
> [!NOTE]
>  Les constructeurs surchargés de la [Microsoft.RuleEngine.RuleSetDeploymentDriver](http://msdn.microsoft.com/library/microsoft.ruleengine.rulesetdeploymentdriver.aspx) classe prennent le nom de la base de données du magasin de règles en tant que paramètre. Cela vous permet de déployer des stratégies dans une base de données pour laquelle votre environnement BizTalk Server n'est pas configuré.  
  
## <a name="using-the-getdeploymentdriver-method"></a>Utilisation de la méthode GetDeploymentDriver  
 Si vous déployez des stratégies à la base de données que votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement est configuré pour utiliser, vous n’êtes pas obligé de créer le **RuleSetDeploymentDriver** objet dans le code. Au lieu de cela, vous pouvez demander le moteur de règles pour créer un **RuleSetDeploymentDriver** objet en appelant le **GetDeploymentDriver** méthode de la **Configuration** classe dans le **System.RuleEngine** espace de noms. L’exemple de code suivant montre comment appeler le **GetDeploymentDriver** méthode :  
  
```  
Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver dd;  
dd = new Microsoft.RuleEngine.Configuration.GetDeploymentDriver();  
```  
  
 Le **GetDeploymentDriver** méthode extrait les valeurs de la **DeploymentDriverAssembly** et **DeploymentDriverClass** des clés de Registre sous **HKEY_ LOCAL_MACHINE\Software\Microsoft\BusinessRules\3.0**et crée une instance de **DeploymentDriverClass**. Le tableau suivant indique les valeurs par défaut de ces deux clés de registre.  
  
|Clé de Registre|Valeur|  
|------------------|-----------|  
|DeploymentDriverAssembly|Microsoft.BizTalk.RuleEngineExtensions|  
|DeploymentDriverClass|Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver|  
  
 Le **RuleSetDeploymentDriver** la classe implémente le **IRuleSetDeploymentDriver** interface. Vous pouvez développer votre propre pilote de déploiement de stratégie en créant une classe qui implémente le **IRuleSetDeploymentDriver** interface et modifier les valeurs pour les clés de Registre ci-dessus comme appropriée.