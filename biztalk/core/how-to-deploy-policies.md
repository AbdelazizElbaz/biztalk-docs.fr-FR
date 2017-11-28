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
# <a name="how-to-deploy-policies"></a><span data-ttu-id="11a74-102">Déploiement des stratégies</span><span class="sxs-lookup"><span data-stu-id="11a74-102">How to Deploy Policies</span></span>
<span data-ttu-id="11a74-103">Vous pouvez déployer des stratégies par programmation à l’aide de la [Microsoft.RuleEngine.RuleSetDeploymentDriver](http://msdn.microsoft.com/library/microsoft.ruleengine.rulesetdeploymentdriver.aspx) classe dans le **Microsoft.RuleEngine.RuleEngineExtensions** espace de noms.</span><span class="sxs-lookup"><span data-stu-id="11a74-103">You can deploy policies programmatically by using the [Microsoft.RuleEngine.RuleSetDeploymentDriver](http://msdn.microsoft.com/library/microsoft.ruleengine.rulesetdeploymentdriver.aspx) class in the **Microsoft.RuleEngine.RuleEngineExtensions** namespace.</span></span> <span data-ttu-id="11a74-104">L’exemple de code suivant montre comment utiliser le [Microsoft.RuleEngine.RuleSetDeploymentDriver](http://msdn.microsoft.com/library/microsoft.ruleengine.rulesetdeploymentdriver.aspx) classe pour déployer une stratégie nommée **LoanProcessing**:</span><span class="sxs-lookup"><span data-stu-id="11a74-104">The following sample code demonstrates how to use the [Microsoft.RuleEngine.RuleSetDeploymentDriver](http://msdn.microsoft.com/library/microsoft.ruleengine.rulesetdeploymentdriver.aspx) class to deploy a policy named **LoanProcessing**:</span></span>  
  
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
>  <span data-ttu-id="11a74-105">Les constructeurs surchargés de la [Microsoft.RuleEngine.RuleSetDeploymentDriver](http://msdn.microsoft.com/library/microsoft.ruleengine.rulesetdeploymentdriver.aspx) classe prennent le nom de la base de données du magasin de règles en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="11a74-105">The overloaded constructors of the [Microsoft.RuleEngine.RuleSetDeploymentDriver](http://msdn.microsoft.com/library/microsoft.ruleengine.rulesetdeploymentdriver.aspx) class take the names of the rule store database as a parameter.</span></span> <span data-ttu-id="11a74-106">Cela vous permet de déployer des stratégies dans une base de données pour laquelle votre environnement BizTalk Server n'est pas configuré.</span><span class="sxs-lookup"><span data-stu-id="11a74-106">This allows you to deploy policies to a database that your BizTalk Server environment is not configured to use.</span></span>  
  
## <a name="using-the-getdeploymentdriver-method"></a><span data-ttu-id="11a74-107">Utilisation de la méthode GetDeploymentDriver</span><span class="sxs-lookup"><span data-stu-id="11a74-107">Using the GetDeploymentDriver Method</span></span>  
 <span data-ttu-id="11a74-108">Si vous déployez des stratégies à la base de données que votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement est configuré pour utiliser, vous n’êtes pas obligé de créer le **RuleSetDeploymentDriver** objet dans le code.</span><span class="sxs-lookup"><span data-stu-id="11a74-108">If you are deploying policies to the database that your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment is configured to use, you do not have to create the **RuleSetDeploymentDriver** object in the code.</span></span> <span data-ttu-id="11a74-109">Au lieu de cela, vous pouvez demander le moteur de règles pour créer un **RuleSetDeploymentDriver** objet en appelant le **GetDeploymentDriver** méthode de la **Configuration** classe dans le **System.RuleEngine** espace de noms.</span><span class="sxs-lookup"><span data-stu-id="11a74-109">Instead, you can request the rule engine to create a **RuleSetDeploymentDriver** object for you by invoking the **GetDeploymentDriver** method of the **Configuration** class in the **System.RuleEngine** namespace.</span></span> <span data-ttu-id="11a74-110">L’exemple de code suivant montre comment appeler le **GetDeploymentDriver** méthode :</span><span class="sxs-lookup"><span data-stu-id="11a74-110">The following sample code demonstrates how to invoke the **GetDeploymentDriver** method:</span></span>  
  
```  
Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver dd;  
dd = new Microsoft.RuleEngine.Configuration.GetDeploymentDriver();  
```  
  
 <span data-ttu-id="11a74-111">Le **GetDeploymentDriver** méthode extrait les valeurs de la **DeploymentDriverAssembly** et **DeploymentDriverClass** des clés de Registre sous **HKEY_ LOCAL_MACHINE\Software\Microsoft\BusinessRules\3.0**et crée une instance de **DeploymentDriverClass**.</span><span class="sxs-lookup"><span data-stu-id="11a74-111">The **GetDeploymentDriver** method retrieves the values of the **DeploymentDriverAssembly** and **DeploymentDriverClass** registry keys under **HKEY_LOCAL_MACHINE\Software\Microsoft\BusinessRules\3.0**, and creates an instance of **DeploymentDriverClass**.</span></span> <span data-ttu-id="11a74-112">Le tableau suivant indique les valeurs par défaut de ces deux clés de registre.</span><span class="sxs-lookup"><span data-stu-id="11a74-112">The following table shows the default values of these two registry keys.</span></span>  
  
|<span data-ttu-id="11a74-113">Clé de Registre</span><span class="sxs-lookup"><span data-stu-id="11a74-113">Registry key</span></span>|<span data-ttu-id="11a74-114">Valeur</span><span class="sxs-lookup"><span data-stu-id="11a74-114">Value</span></span>|  
|------------------|-----------|  
|<span data-ttu-id="11a74-115">DeploymentDriverAssembly</span><span class="sxs-lookup"><span data-stu-id="11a74-115">DeploymentDriverAssembly</span></span>|<span data-ttu-id="11a74-116">Microsoft.BizTalk.RuleEngineExtensions</span><span class="sxs-lookup"><span data-stu-id="11a74-116">Microsoft.BizTalk.RuleEngineExtensions</span></span>|  
|<span data-ttu-id="11a74-117">DeploymentDriverClass</span><span class="sxs-lookup"><span data-stu-id="11a74-117">DeploymentDriverClass</span></span>|<span data-ttu-id="11a74-118">Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver</span><span class="sxs-lookup"><span data-stu-id="11a74-118">Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver</span></span>|  
  
 <span data-ttu-id="11a74-119">Le **RuleSetDeploymentDriver** la classe implémente le **IRuleSetDeploymentDriver** interface.</span><span class="sxs-lookup"><span data-stu-id="11a74-119">The **RuleSetDeploymentDriver** class implements the **IRuleSetDeploymentDriver** interface.</span></span> <span data-ttu-id="11a74-120">Vous pouvez développer votre propre pilote de déploiement de stratégie en créant une classe qui implémente le **IRuleSetDeploymentDriver** interface et modifier les valeurs pour les clés de Registre ci-dessus comme appropriée.</span><span class="sxs-lookup"><span data-stu-id="11a74-120">You can develop your own policy deployment driver by creating a class that implements the **IRuleSetDeploymentDriver** interface and change the values for the registry keys described above as appropriate.</span></span>