---
title: "Sélectionnez un schéma d’URI et le format d’adressage lors de l’utilisation de WCF LOB Adapter SDK | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bb4feee-3d39-43ca-82ac-aba38c13bc69
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9990facf6a23f4abea37ee9ce9758a7333eaca61
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="select-a-uri-scheme-and-addressing-format-when-using-the-wcf-lob-adapter-sdk"></a>Sélectionnez un schéma d’URI et le format d’adressage lors de l’utilisation de WCF LOB Adapter SDK
Un identificateur de ressource uniforme (URI) identifie de façon unique les ressources comme un service Web ou, dans le cas d’un adaptateur développées avec le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], le système pour vous connecter à, ainsi que l’action à effectuer. Cette section fournit une recommandation sur la façon de construire un URI pour décrivent de façon unique l’adresse de point de terminaison et l’action de votre adaptateur.  
  
## <a name="anatomy-of-a-uri"></a>Anatomie d’un URI  
 Un URI se compose de trois composants suivants :  
  
-   **Nom du schéma** est la partie de tête de la chaîne d’URI et est le premier niveau de la structure d’affectation de noms ; exemples incluent http, urn et contoso.  
  
-   **Partie hiérarchique** se compose d’informations qui sont généralement hiérarchique et peuvent contenir l’autorité facultatif, nom d’hôte et les informations de port. Par exemple www.microsoft.com et le nom d’utilisateur =User@microsoft.com:4099.  
  
-   **Requête** contient des informations facultatives marqués avec un point d’interrogation ( ?) et généralement regroupés en tant que paires clé/valeur séparées par une esperluette (&). Par exemple, contoso://microsoft.com/functions?name=Find.  
  
-   **Fragment** est utilisé pour stocker les informations d’identification supplémentaires qui peuvent être requises par l’adaptateur. Le fragment est séparé par un dièse (#) ; par exemple, contoso://microsoft.com/functions?name=Find#public.  
  
 Vous ne pouvez pas utiliser toutes les fonctionnalités fournies par la syntaxe d’URI.  
  
## <a name="designing-the-uri"></a>Conception de l’URI  
 En tant que développeur d’adaptateur, vous devrez imaginer un URI correspondant à votre système de line-of-business cible. Lorsque vous concevez votre URI, il est important pour le rendre unique et significatif.  
  
 Un URI unique est celle qui n’est pas en conflit avec l’URI existant dans une organisation et entre les autres entreprises et Internet. Par exemple, en choisissant un nom de schéma comme « http » ou « afs » qui peut être reconnu actuellement ou déjà largement utilisé peut entraîner des problèmes opérationnels ou connexion, car les demandes peuvent être routées vers un autre système et non à votre carte.  
  
 Un autre aspect important de la conception de l’URI est qu’il soit explicite à l’audience de développeur qui utilise votre adaptateur. Par exemple, si vous écrivez un adaptateur pour un médical de système de traitement des revendications, vous pouvez créer un modèle URI qui inclut le nom de votre société, les revendications de la cible du traitement de nom du système et la version du système : northwind.contoso.cps.v1.0://.  
  
## <a name="connecting-to-the-target-system"></a>Connexion au système cible  
 Chaînes de connexion ont la syntaxe suivante :  
  
 **\<schéma\>: //[userinfo « @ »]\<LOB de chaîne de connexion\>**  
  
 Par exemple, vous pouvez se connecter au catalogue contoso (une ligne de l’exemple d’application d’entreprise) de système de commande à l’aide de ce qui suit :  
  
 **Northwind.contoso.v1.0://\<nom_serveur\>? Catalogue = Contoso & Integrated Security = True**  
  
 Vous pouvez également fournir des informations de l’autorité facultatif dans l’URI, y compris le nom d’utilisateur et mot de passe et autres informations d’identification importantes. Toutefois, cela peut présenter un risque de sécurité.  
  
> [!CAUTION]
>  Ne passez pas d’informations d’identification utilisateur et d’autres informations sensibles dans l’URI. Cette information peut être interceptée ni affichée par des utilisateurs non autorisés.  
  
## <a name="see-also"></a>Voir aussi  
 [Planifier et concevoir un adaptateur à l’aide de WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-an-adapter-using-the-wcf-lob-adapter-sdk.md)