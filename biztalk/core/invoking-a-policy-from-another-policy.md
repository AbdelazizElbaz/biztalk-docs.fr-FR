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
# <a name="invoking-a-policy-from-another-policy"></a>Appel d'une stratégie à partir d'une autre
Vous pouvez appeler une stratégie (enfant) à partir d'une autre stratégie (parent) à l'aide de l'une des méthodes suivantes :  
  
-   Appel de la **Policy.Execute** (méthode) directement à partir de la stratégie parent  
  
-   Appeler une méthode d’un composant de .NET d’assistance qui encapsule le **Policy.Execute** méthode à partir de la stratégie parent  
  
 L’avantage de l’utilisation de la seconde méthode est que vous pouvez ajouter le code de pré-traitement et de post-traitement à la **Policy.Execute** (méthode). Par exemple, vous pouvez créer les faits requis à partir de la stratégie enfant de cette méthode de wrapper. Les sections suivantes fournissent un exemple pour chaque méthode.  
  
## <a name="invoking-the-policyexecute-method-directly-from-the-parent-policy"></a>Appel de la méthode Policy.Execute directement à partir de la stratégie parent  
 Cette section présente les principales étapes à suivre pour appeler la stratégie enfant à partir de la stratégie parent à l’aide de la **Policy.Execute** directement la méthode.  
  
### <a name="adding-the-policyexecute-action-to-the-parent-policy"></a>Ajout de l'action Policy.Execute à la stratégie parent  
 La procédure suivante présente les étapes pour ajouter la **Policy.Execute** méthode en tant qu’action à la stratégie parent qui envoie un document XML en tant que fait à la stratégie enfant.  
  
##### <a name="to-add-the-policyexecute-method-as-an-action-to-a-policy"></a>Pour ajouter la méthode Policy.Execute en tant qu'action à une stratégie  
  
1.  Dans la fenêtre Explorateur de faits, cliquez sur le **Classes .NET** onglet.  
  
2.  Avec le bouton droit **assemblys .NET**, puis cliquez sur **Parcourir**.  
  
3.  Sélectionnez **Microsoft.RuleEngine** à partir de la **assemblys .NET** liste, puis cliquez sur **OK**.  
  
4.  Développez **stratégie**.  
  
5.  Faites glisser **Execute (Object facts)** ou **Execute (Object facts, IRuleSetTrackingInterceptor trackingInterceptor)** vers le volet THEN.  
  
6.  Cliquez sur le **schémas XML** nœud.  
  
    > [!NOTE]
    >  Dans cet exemple de scénario, un document XML qui est envoyé en tant que fait à la stratégie parent l'est également à la stratégie enfant. Vous pouvez à la place appeler une méthode .NET qui crée les faits pour la stratégie enfant.  
  
7.  Avec le bouton droit **schémas**, puis cliquez sur **Parcourir**.  
  
8.  Sélectionnez le schéma pour le document XML que vous souhaitez passer en tant que fait, puis cliquez sur **ouvrir**.  
  
9. Faites glisser  *\<nom de schéma >*.xsd sur le premier argument de la **Policy.Execute** méthode pour transmettre le document XML qui est passé à la stratégie parent en tant que fait à la stratégie enfant.  
  
10. Si vous utilisez la **Execute** méthode qui n’accepte pas les **IRuleSetTrackingInterceptor** comme deuxième argument, ignorez les étapes suivantes.  
  
11. Cliquez sur le **Classes .NET** onglet.  
  
12. Faites glisser **DebugTrackingInterceptor** dans **Microsoft.RuleEngine** pour le deuxième argument de la **Policy.Execute** (méthode).  
  
    > [!NOTE]
    >  Si vous effectuez cette action, le client doit passer une instance de la **DebugTrackingInterceptor** classe en tant que fait à la stratégie parent, qui à son tour transmet l’instance en tant que fait à la stratégie enfant. Au lieu de cela, vous pourriez faire glisser le constructeur de la **DebugTrackingInterceptor** classe afin que l’instance est créée automatiquement pour vous.  
  
### <a name="modifying-the-client-application-that-invokes-the-parent-policy"></a>Modification de l'application client appelant la stratégie parent  
 Le client qui appelle la stratégie parent crée une instance de la **stratégie** classe avec le nom de la stratégie enfant en tant que paramètre et le passe en tant que fait à la stratégie parent, ainsi que d’autres faits. L'exemple de code suivant illustre cette action :  
  
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
  
 Si le client est une orchestration BizTalk, vous devez placer le code pour créer des faits dans un **Expression** mettre en forme et transmettez les faits en tant que paramètres à la **appeler règles** forme.  
  
## <a name="invoking-a-net-wrapper-method-from-the-parent-policy"></a>Appel d'une méthode de wrapper .NET à partir de la stratégie parent  
 Cette section présente les principales étapes à suivre pour appeler une méthode .NET qui encapsule l’appel à la **Policy.Execute** méthode à partir de la stratégie parent.  
  
### <a name="creating-the-utility-net-class"></a>Création de la classe d'utilitaire .NET  
  
##### <a name="to-create-the-utility-class"></a>Pour créer la classe d'utilitaire  
  
1.  Créez un projet de bibliothèque de classes .NET, puis ajoutez une classe à celui-ci.  
  
2.  Ajoutez une méthode statique qui appelle le **Policy.Execute** méthode à appeler la stratégie dont le nom est passé en tant que paramètre, comme indiqué dans l’exemple de code suivant :  
  
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
  
3.  Assurez-vous que le **StaticSupport** clé de Registre est définie sur 1 ou 2. Pour plus d’informations sur la clé de Registre, consultez [appel des membres statiques d’une classe](../core/invoking-static-members-of-a-class.md).  
  
    > [!NOTE]
    >  Vous pouvez utiliser une méthode d'instance à la place d'une méthode statique. Si vous utilisez une méthode d'instance, souvenez-vous que le client doit envoyer une instance de la classe d'assistance .NET en tant que fait à la stratégie parent.  
  
### <a name="modifying-the-client-application"></a>Modification de l'application client  
 Le client appelle la stratégie parent, et celle-ci appelle la méthode d'assistance qui a sont tour appelle la stratégie enfant. L'exemple de code pour le client se présente comme suit :  
  
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
>  Si vous utilisez une méthode d'instance, le client doit créer une instance de la classe d'assistance .NET et l'envoyer en tant que fait à la stratégie parent.  
  
> [!NOTE]
>  Si le client est une orchestration BizTalk, vous devez placer le code pour créer des faits dans un **Expression** mettre en forme et transmettez les faits en tant que paramètres à la **appeler règles** forme.