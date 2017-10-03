---
title: "Comment arrêter un adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfba2b61-b89f-41cd-a014-4e96daec6516
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd2621e15803dd5f6e8f449de530e84df1bc1b9d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-terminate-an-adapter"></a>Comment arrêter un adaptateur
Les rubriques suivantes fournissent des instructions sur la façon appropriée d'arrêter un adaptateur.  
  
## <a name="terminating-an-adapter"></a>Arrêt d'un adaptateur  
 Lorsque le moteur de messagerie s’arrête, il appelle **IBTTransportControl**. **Arrêter** sur chaque adaptateur in-process. Après le retour de la méthode, BizTalk Server détruit l'adaptateur. Pour les adaptateurs natifs, cette destruction se produit immédiatement, tandis que pour les adaptateurs gérés, le moment précis de cette destruction est moins déterministe, en raison du processus de nettoyage de la mémoire .NET. L’adaptateur doit bloquer **Terminate** et effectuer tout travail de nettoyage jusqu'à ce qu’il est prêt à être détruit.  
  
## <a name="terminating-isolated-receive-adapters"></a>Arrêt d'adaptateurs de réception isolés  
 Isolé de réception cartes ne sont pas **Terminate** appelée sur ces derniers, car ils ne sont pas hébergés dans le service BizTalk. Au lieu de cela, ils doivent appeler **IBTTransportProxy**. **TerminateIsolatedReceiver** pour informer le moteur de messagerie qu’ils sont sur le point d’arrêt.  
  
## <a name="clean-up-com-objects-by-using-marshalreleasecomobject"></a>Nettoyage d'objets COM à l'aide de Marshal.ReleaseComObject  
 Lors de la rédaction de code managé utilisant des objets COM, le CLR (Common Language Runtime) génère des objets proxy contenant les références aux objets COM. Les objets proxy sont des objets managés soumis aux règles habituelles du nettoyage de la mémoire. Le problème vient du fait que le garbage collector accède uniquement à la mémoire allouée par les modes d'exécution .NET et qu'il ne tient pas compte de l'objet COM. Étant donné que les objets proxy sont petits, un grand objet COM peut être oublié dans la mémoire, car le garbage collector CLR ne l'a pas pris en considération.  
  
 Pour éviter ce problème, explicitement libérer des objets COM sous-jacents lorsque vous avez terminé avec eux, en particulier les **IBTTransportBatch** objets. Pour cela, vous devez appeler **marshaler**. **ReleaseComObject**.  
  
> [!NOTE]
>  **ReleaseComObject** retourne le nombre de références restantes et libère uniquement l’objet COM lorsque la valeur retournée est zéro. Souvent **ReleaseComObject** est appelée dans une boucle afin de garantir que l’objet est libéré. Une fois cette opération terminée, vous devez appeler **SuppressFinalize** sur cet objet, car il n’a rien à finaliser. La dernière étape consiste à vérifier l'existence de l'objet COM.  
  
 Le code suivant présente le processus décrit ci-dessus :  
  
```  
if (Marshal.IsComObject (batch))  
(  
While (0 <Marshal.ReleaseComObject(batch)  
;  
GC.SuppressFinalize (batch);  
  
```  
  
 Libérer explicitement les **IBTTransportBatch** objet retourné à partir de **GetBatch** peut apporter une amélioration significative des performances.  
  
## <a name="always-use-terminate-when-closing-an-adapter"></a>Utilisation systématique de Terminate lors de l'arrêt d'un adaptateur  
 Pour que BizTalk Server reconnaisse votre code comme une carte, vous devez implémenter une interface appelée **IBTTransportControl**. Cette interface détermine la façon dont BizTalk Server communique avec votre adaptateur. Elle est définie de la façon suivante :  
  
```  
public interface IBTTransportControl   
{  
void Initialize(IBTTransportProxy transportProxy);  
void Terminate();  
}  
```  
  
 L’interface contient deux méthodes, **initialiser** et **Terminate**.  
  
### <a name="initialize"></a>Initialiser  
 BizTalk Server appelle le **initialiser** méthode après avoir chargé l’assembly d’adaptateur. Il procède ainsi pour transmettre le proxy de transport (le handle principal vers BizTalk Server) à l'adaptateur. L’implémentation de **initialiser** stocke simplement le proxy de transport dans une variable membre.  
  
### <a name="terminate"></a>Terminate  
 BizTalk Server appelle le **Terminate** méthode lors de l’arrêt du service pour permettre à l’adaptateur le temps de terminer l’exécution de tous les lots. L’implémentation de la **Terminate** méthode beaucoup plus compliqué.  
  
 L’adaptateur ne doit pas répondre à une **Terminate** appeler jusqu'à la fin de n’importe quel travail en attente, il a. Lorsque BizTalk Server appelle **Terminate**, l’adaptateur doit essayer d’arrêter toutes ses tâches en cours et ne démarre pas de nouvelles.  
  
 Étant donné que **Terminate** est appelée dans le cadre de l’arrêt du service, le Gestionnaire de contrôle de service termine le processus si l’adaptateur bloque perpétuelle **Terminate**. Dans ce cas, vous recevez un avertissement du gestionnaire de contrôle de service lorsqu'il arrête le service BizTalk Server. Si possible, évitez d'arrêter l'adaptateur prématurément. Si l'adaptateur ne traite pas le processus d'arrêt de façon appropriée et que des threads sont toujours en cours d'exécution au début du processus d'arrêt, il se peut que vous receviez un message de violation d'accès de la part de BizTalk Server au moment de l'arrêt.  
  
 En raison de la nature asynchrone de l'interface vers BizTalk Server, il est probable que, en condition de charge, de nombreux lots, et donc de nombreux threads, soient encore en cours d'exécution. Le **Terminate** appel doit être implémenté pour attendre la fin de chaque lot que l’adaptateur a correctement exécuté sur le serveur BizTalk avant de continuer. La fin du lot est signalée par le **BatchComplete** rappel à partir de BizTalk Server. Le **Terminate** appel doit attendre tous les rappels **BatchComplete** doit se produire. En outre, l'exécution des lots doit être réussie. Autrement dit, l’appel à **IBTTransportBatch**::**fait** ne doit pas échouer. Si l’appel à **IBTTransportBatch**::**fait** échoue, il n’existe aucun rappel de lot.  
  
 Ensuite, vous devez ajouter du code de synchronisation à votre adaptateur, procédure relativement simple.  
  
 Une méthode simple consiste à implémenter un objet de synchronisation composé avec **entrez** et **laisser** méthodes pour les threads de travail et un **Terminer** méthode qui entraîne un blocage lors de l’une thread est toujours à l’intérieur d’exécution. (D’ailleurs, la solution est très similaire à la structure de lecteurs multiples, seul l’enregistreur familier où les threads de travail peuvent être considérés comme des lecteurs et la **arrêter** le writer de la méthode.)  
  
 Le **Terminer** méthode est la suivante :  
  
```  
void terminate ()  
{  
this.control.Terminate();  
}  
```  
  
 Pour chaque thread de travail :  
  
```  
If (!this.control.Enter())  
return; // we can’t enter because Terminate has been called  
try  
{  
//  create and fill batch  
batch.Done();  
}  
catch (Exception)  
{  
//  we are not expecting a callback  
This.control.Leave();  
}  
```  
  
 Dans le rappel émis par BizTalk Server :  
  
```  
batchComplete (…)  
{  
//  the callback from BizTalk Server  
//  process results  
this.control.Leave();  
}  
```  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est fourni avec l'exemple de code ControlledTermination.cs, dans l'exemple de l'adaptateur de base (Base Adapter), qui illustre le mécanisme de synchronisation décrit ici.