---
title: "Appel d’une stratégie à partir d’une autre stratégie | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5bf658a-02a1-426a-abe5-8c9de673cf0d
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b03204b9de4b763f516b7fb22ada1f4f3f6173a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invoking-a-policy-from-another-policy"></a><span data-ttu-id="95363-102">Appel d'une stratégie à partir d'une autre</span><span class="sxs-lookup"><span data-stu-id="95363-102">Invoking a Policy from Another Policy</span></span>
<span data-ttu-id="95363-103">Vous pouvez appeler une stratégie (enfant) à partir d'une autre stratégie (parent) à l'aide de l'une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="95363-103">You can invoke a policy (child) from another policy (parent) by using one of the following methods:</span></span>  
  
-   <span data-ttu-id="95363-104">Appel de la **Policy.Execute** (méthode) directement à partir de la stratégie parent</span><span class="sxs-lookup"><span data-stu-id="95363-104">Calling the **Policy.Execute** method directly from the parent policy</span></span>  
  
-   <span data-ttu-id="95363-105">Appeler une méthode d’un composant de .NET d’assistance qui encapsule le **Policy.Execute** méthode à partir de la stratégie parent</span><span class="sxs-lookup"><span data-stu-id="95363-105">Calling a method of a helper .NET component that wraps the **Policy.Execute** method from the parent policy</span></span>  
  
 <span data-ttu-id="95363-106">L’avantage de l’utilisation de la seconde méthode est que vous pouvez ajouter le code de pré-traitement et de post-traitement à la **Policy.Execute** (méthode).</span><span class="sxs-lookup"><span data-stu-id="95363-106">The advantage of using the second method is that you can add pre-processing and post-processing code to the **Policy.Execute** method.</span></span> <span data-ttu-id="95363-107">Par exemple, vous pouvez créer les faits requis à partir de la stratégie enfant de cette méthode de wrapper.</span><span class="sxs-lookup"><span data-stu-id="95363-107">For example, you can create any facts required from the child policy in this wrapper method.</span></span> <span data-ttu-id="95363-108">Les sections suivantes fournissent un exemple pour chaque méthode.</span><span class="sxs-lookup"><span data-stu-id="95363-108">The following sections provide an example for each method.</span></span>  
  
## <a name="invoking-the-policyexecute-method-directly-from-the-parent-policy"></a><span data-ttu-id="95363-109">Appel de la méthode Policy.Execute directement à partir de la stratégie parent</span><span class="sxs-lookup"><span data-stu-id="95363-109">Invoking the Policy.Execute Method Directly from the Parent Policy</span></span>  
 <span data-ttu-id="95363-110">Cette section présente les principales étapes à suivre pour appeler la stratégie enfant à partir de la stratégie parent à l’aide de la **Policy.Execute** directement la méthode.</span><span class="sxs-lookup"><span data-stu-id="95363-110">This section presents the high-level steps to invoke the child policy from the parent policy by using the **Policy.Execute** method directly.</span></span>  
  
### <a name="adding-the-policyexecute-action-to-the-parent-policy"></a><span data-ttu-id="95363-111">Ajout de l'action Policy.Execute à la stratégie parent</span><span class="sxs-lookup"><span data-stu-id="95363-111">Adding the Policy.Execute Action to the Parent Policy</span></span>  
 <span data-ttu-id="95363-112">La procédure suivante présente les étapes pour ajouter la **Policy.Execute** méthode en tant qu’action à la stratégie parent qui envoie un document XML en tant que fait à la stratégie enfant.</span><span class="sxs-lookup"><span data-stu-id="95363-112">The following procedure has steps to add the **Policy.Execute** method as an action to the parent policy that passes an XML document as a fact to the child policy.</span></span>  
  
##### <a name="to-add-the-policyexecute-method-as-an-action-to-a-policy"></a><span data-ttu-id="95363-113">Pour ajouter la méthode Policy.Execute en tant qu'action à une stratégie</span><span class="sxs-lookup"><span data-stu-id="95363-113">To add the Policy.Execute method as an action to a policy</span></span>  
  
1.  <span data-ttu-id="95363-114">Dans la fenêtre Explorateur de faits, cliquez sur le **Classes .NET** onglet.</span><span class="sxs-lookup"><span data-stu-id="95363-114">In the Facts Explorer window, click the **.NET Classes** tab.</span></span>  
  
2.  <span data-ttu-id="95363-115">Avec le bouton droit **assemblys .NET**, puis cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="95363-115">Right-click **.NET Assemblies**, and then click **Browse**.</span></span>  
  
3.  <span data-ttu-id="95363-116">Sélectionnez **Microsoft.RuleEngine** à partir de la **assemblys .NET** liste, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="95363-116">Select **Microsoft.RuleEngine** from the **.NET Assemblies** list, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="95363-117">Développez **stratégie**.</span><span class="sxs-lookup"><span data-stu-id="95363-117">Expand **Policy**.</span></span>  
  
5.  <span data-ttu-id="95363-118">Faites glisser **Execute (Object facts)** ou **Execute (Object facts, IRuleSetTrackingInterceptor trackingInterceptor)** vers le volet THEN.</span><span class="sxs-lookup"><span data-stu-id="95363-118">Drag **Execute(Object facts)** or **Execute(Object facts, IRuleSetTrackingInterceptor trackingInterceptor)** to the THEN pane.</span></span>  
  
6.  <span data-ttu-id="95363-119">Cliquez sur le **schémas XML** nœud.</span><span class="sxs-lookup"><span data-stu-id="95363-119">Click the **XML Schemas** node.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="95363-120">Dans cet exemple de scénario, un document XML qui est envoyé en tant que fait à la stratégie parent l'est également à la stratégie enfant.</span><span class="sxs-lookup"><span data-stu-id="95363-120">In this sample scenario, an XML document that is submitted as a fact to the parent policy is passed as a fact to the child policy.</span></span> <span data-ttu-id="95363-121">Vous pouvez à la place appeler une méthode .NET qui crée les faits pour la stratégie enfant.</span><span class="sxs-lookup"><span data-stu-id="95363-121">Instead, you can invoke a .NET method that creates the facts for the child policy.</span></span>  
  
7.  <span data-ttu-id="95363-122">Avec le bouton droit **schémas**, puis cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="95363-122">Right-click **Schemas**, and then click **Browse**.</span></span>  
  
8.  <span data-ttu-id="95363-123">Sélectionnez le schéma pour le document XML que vous souhaitez passer en tant que fait, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="95363-123">Select the schema for the XML document you want to pass as a fact, and then click **Open**.</span></span>  
  
9. <span data-ttu-id="95363-124">Faites glisser  *\<nom de schéma >*.xsd sur le premier argument de la **Policy.Execute** méthode pour transmettre le document XML qui est passé à la stratégie parent en tant que fait à la stratégie enfant.</span><span class="sxs-lookup"><span data-stu-id="95363-124">Drag *\<Schema name>*.xsd to the first argument of the **Policy.Execute** method to pass the XML document that is passed to the parent policy as a fact to the child policy.</span></span>  
  
10. <span data-ttu-id="95363-125">Si vous utilisez la **Execute** méthode qui n’accepte pas les **IRuleSetTrackingInterceptor** comme deuxième argument, ignorez les étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="95363-125">If you use the **Execute** method that does not take the **IRuleSetTrackingInterceptor** as the second argument, skip the following steps.</span></span>  
  
11. <span data-ttu-id="95363-126">Cliquez sur le **Classes .NET** onglet.</span><span class="sxs-lookup"><span data-stu-id="95363-126">Click the **.NET Classes** tab.</span></span>  
  
12. <span data-ttu-id="95363-127">Faites glisser **DebugTrackingInterceptor** dans **Microsoft.RuleEngine** pour le deuxième argument de la **Policy.Execute** (méthode).</span><span class="sxs-lookup"><span data-stu-id="95363-127">Drag **DebugTrackingInterceptor** in **Microsoft.RuleEngine** to the second argument of the **Policy.Execute** method.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="95363-128">Si vous effectuez cette action, le client doit passer une instance de la **DebugTrackingInterceptor** classe en tant que fait à la stratégie parent, qui à son tour transmet l’instance en tant que fait à la stratégie enfant.</span><span class="sxs-lookup"><span data-stu-id="95363-128">If you perform this action, the client must pass an instance of the **DebugTrackingInterceptor** class as a fact to the parent policy, which in turn passes the instance as a fact to the child policy.</span></span> <span data-ttu-id="95363-129">Au lieu de cela, vous pourriez faire glisser le constructeur de la **DebugTrackingInterceptor** classe afin que l’instance est créée automatiquement pour vous.</span><span class="sxs-lookup"><span data-stu-id="95363-129">Instead you could drag the constructor of the **DebugTrackingInterceptor** class so that the instance is automatically created for you.</span></span>  
  
### <a name="modifying-the-client-application-that-invokes-the-parent-policy"></a><span data-ttu-id="95363-130">Modification de l'application client appelant la stratégie parent</span><span class="sxs-lookup"><span data-stu-id="95363-130">Modifying the Client Application that Invokes the Parent Policy</span></span>  
 <span data-ttu-id="95363-131">Le client qui appelle la stratégie parent crée une instance de la **stratégie** classe avec le nom de la stratégie enfant en tant que paramètre et le passe en tant que fait à la stratégie parent, ainsi que d’autres faits.</span><span class="sxs-lookup"><span data-stu-id="95363-131">The client that invokes the parent policy creates an instance of the **Policy** class with the child policy name as a parameter and passes it as a fact to the parent policy along with other facts.</span></span> <span data-ttu-id="95363-132">L'exemple de code suivant illustre cette action :</span><span class="sxs-lookup"><span data-stu-id="95363-132">The following sample code illustrates this action:</span></span>  
  
```  
DebugTrackingInterceptor dti = new DebugTrackingInterceptor("PolicyTracking.txt");  
Policy policy = new Policy("ParentPolicy");  
object[] facts = new object[3];  
facts[0] = txd;  
facts[1] = new Policy("ChildPolicy");  
facts[2] = new DebugTrackingInterceptor("PolicyTracking2.txt");  
policy.Execute(facts, dti);  
policy.Dispose();  
```  
  
 <span data-ttu-id="95363-133">Si le client est une orchestration BizTalk, vous devez placer le code pour créer des faits dans un **Expression** mettre en forme et transmettez les faits en tant que paramètres à la **appeler règles** forme.</span><span class="sxs-lookup"><span data-stu-id="95363-133">If the client is a BizTalk orchestration, you may need to place the code to create facts in an **Expression** shape, and then pass the facts as parameters to the **Call Rules** shape.</span></span>  
  
## <a name="invoking-a-net-wrapper-method-from-the-parent-policy"></a><span data-ttu-id="95363-134">Appel d'une méthode de wrapper .NET à partir de la stratégie parent</span><span class="sxs-lookup"><span data-stu-id="95363-134">Invoking a .NET Wrapper Method from the Parent Policy</span></span>  
 <span data-ttu-id="95363-135">Cette section présente les principales étapes à suivre pour appeler une méthode .NET qui encapsule l’appel à la **Policy.Execute** méthode à partir de la stratégie parent.</span><span class="sxs-lookup"><span data-stu-id="95363-135">This section presents the high-level steps to invoke a .NET method that wraps the call to the **Policy.Execute** method from the parent policy.</span></span>  
  
### <a name="creating-the-utility-net-class"></a><span data-ttu-id="95363-136">Création de la classe d'utilitaire .NET</span><span class="sxs-lookup"><span data-stu-id="95363-136">Creating the Utility .NET Class</span></span>  
  
##### <a name="to-create-the-utility-class"></a><span data-ttu-id="95363-137">Pour créer la classe d'utilitaire</span><span class="sxs-lookup"><span data-stu-id="95363-137">To create the utility class</span></span>  
  
1.  <span data-ttu-id="95363-138">Créez un projet de bibliothèque de classes .NET, puis ajoutez une classe à celui-ci.</span><span class="sxs-lookup"><span data-stu-id="95363-138">Create a .NET class library project, and then add a class to the project.</span></span>  
  
2.  <span data-ttu-id="95363-139">Ajoutez une méthode statique qui appelle le **Policy.Execute** méthode à appeler la stratégie dont le nom est passé en tant que paramètre, comme indiqué dans l’exemple de code suivant :</span><span class="sxs-lookup"><span data-stu-id="95363-139">Add a static method that calls the **Policy.Execute** method to invoke the policy whose name is passed as a parameter, as shown in the following sample code:</span></span>  
  
    ```  
    public static void Execute(string policyName, TypedXmlDocument txd)  
    {  
        DebugTrackingInterceptor dti = new   DebugTrackingInterceptor("PolicyTracking.txt");  
        Policy policy = new Policy("ParentPolicy");  
        object[] facts = new object[3];  
        facts[0] = txd;  
        facts[1] = new Policy("ChildPolicy");  
        facts[2] = new DebugTrackingInterceptor("PolicyTracking2.txt");  
        policy.Execute(facts, dti);  
        policy.Dispose();  
    }   
    ```  
  
3.  <span data-ttu-id="95363-140">Assurez-vous que le **StaticSupport** clé de Registre est définie sur 1 ou 2.</span><span class="sxs-lookup"><span data-stu-id="95363-140">Make sure that the **StaticSupport** registry key is set to 1 or 2.</span></span> <span data-ttu-id="95363-141">Pour plus d’informations sur la clé de Registre, consultez [appel des membres statiques d’une classe](../core/invoking-static-members-of-a-class.md).</span><span class="sxs-lookup"><span data-stu-id="95363-141">For more information about the registry key, see [Invoking Static Members of a Class](../core/invoking-static-members-of-a-class.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="95363-142">Vous pouvez utiliser une méthode d'instance à la place d'une méthode statique.</span><span class="sxs-lookup"><span data-stu-id="95363-142">You can use an instance method instead of a static method.</span></span> <span data-ttu-id="95363-143">Si vous utilisez une méthode d'instance, souvenez-vous que le client doit envoyer une instance de la classe d'assistance .NET en tant que fait à la stratégie parent.</span><span class="sxs-lookup"><span data-stu-id="95363-143">Remember that, if you use an instance method, the client must pass an instance of the helper .NET class as a fact to the parent policy.</span></span>  
  
### <a name="modifying-the-client-application"></a><span data-ttu-id="95363-144">Modification de l'application client</span><span class="sxs-lookup"><span data-stu-id="95363-144">Modifying the Client Application</span></span>  
 <span data-ttu-id="95363-145">Le client appelle la stratégie parent, et celle-ci appelle la méthode d'assistance qui a sont tour appelle la stratégie enfant.</span><span class="sxs-lookup"><span data-stu-id="95363-145">The client invokes the parent policy, and the parent policy invokes the helper method that invokes the child policy.</span></span> <span data-ttu-id="95363-146">L'exemple de code pour le client se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="95363-146">The sample code for the client is as follows:</span></span>  
  
```  
facts[0] = txd;  
facts[1] = new PolicyExecutor(txd);  
//call the first or parent policy  
Policy policy = new Policy(policyName);  
DebugTrackingInterceptor dti = new DebugTrackingInterceptor("PolicyTracking.txt");  
policy.Execute(facts, dti);  
policy.Dispose();  
```  
  
> [!NOTE]
>  <span data-ttu-id="95363-147">Si vous utilisez une méthode d'instance, le client doit créer une instance de la classe d'assistance .NET et l'envoyer en tant que fait à la stratégie parent.</span><span class="sxs-lookup"><span data-stu-id="95363-147">If the method is an instance method, the client must create an instance of the helper .NET class, and pass it as a fact to the parent policy.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95363-148">Si le client est une orchestration BizTalk, vous devez placer le code pour créer des faits dans un **Expression** mettre en forme et transmettez les faits en tant que paramètres à la **appeler règles** forme.</span><span class="sxs-lookup"><span data-stu-id="95363-148">If the client is a BizTalk orchestration, you may need to place the code to create facts in an **Expression** shape, and then pass the facts as parameters to the **Call Rules** shape.</span></span>