---
redirect_url: /biztalk/core/creating-peoplesoft-send-handlers/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: ec518c16383d847bf13706a6469b038b447c1543
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="how-to-create-send-ports-for-peoplesoft-enterprise"></a><span data-ttu-id="3815d-101">Création des ports d'envoi pour PeopleSoft Enterprise</span><span class="sxs-lookup"><span data-stu-id="3815d-101">How to Create Send Ports for PeopleSoft Enterprise</span></span>
<span data-ttu-id="3815d-102">Suivez les étapes ci-après pour créer un port d'envoi à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="3815d-102">Follow these steps to create a send port using BizTalk Server Administration Console.</span></span>  
  
## <a name="creating-a-send-port"></a><span data-ttu-id="3815d-103">Création d'un port d'envoi</span><span class="sxs-lookup"><span data-stu-id="3815d-103">Creating a Send Port</span></span>  
  
#### <a name="to-create-a-send-port"></a><span data-ttu-id="3815d-104">Pour créer un port d’envoi</span><span class="sxs-lookup"><span data-stu-id="3815d-104">To create a send port</span></span>  
  
1.  <span data-ttu-id="3815d-105">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez souhaité application.</span><span class="sxs-lookup"><span data-stu-id="3815d-105">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the desired application.</span></span>  
  
2.  <span data-ttu-id="3815d-106">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.</span><span class="sxs-lookup"><span data-stu-id="3815d-106">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
3.  <span data-ttu-id="3815d-107">Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="3815d-107">In the **Send Port Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="3815d-108">Tapez un nom pour le port d’envoi, par exemple, `SSOSendToPeopleSoft`.</span><span class="sxs-lookup"><span data-stu-id="3815d-108">Type a name for the send port, for example, `SSOSendToPeopleSoft`.</span></span>  
  
    2.  <span data-ttu-id="3815d-109">À partir de la **Type** la liste déroulante, sélectionnez **PeopleSoft**.</span><span class="sxs-lookup"><span data-stu-id="3815d-109">From the **Type** drop-down list, select **PeopleSoft**.</span></span>  
  
    3.  <span data-ttu-id="3815d-110">À partir de la **Gestionnaire d’envoi** liste déroulante, sélectionnez l’URI.</span><span class="sxs-lookup"><span data-stu-id="3815d-110">From the **Send handler** drop-down list, select the URI.</span></span>  
  
    4.  <span data-ttu-id="3815d-111">Dans la liste déroulante Pipeline d’envoi, sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="3815d-111">From the Send Pipeline drop-down list, select **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.</span></span>  
  
    5.  <span data-ttu-id="3815d-112">À partir de la **Pipeline de réception** la liste déroulante, sélectionnez **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="3815d-112">From the **Receive Pipeline** drop-down list, select **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.</span></span>  
  
    6.  <span data-ttu-id="3815d-113">Cliquez sur **configurer** pour configurer le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="3815d-113">Click **Configure** to configure the send port.</span></span>  
  
4.  <span data-ttu-id="3815d-114">Dans le **propriétés du Transport PeopleSoft** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="3815d-114">In the **PeopleSoft Transport Properties** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="3815d-115">Développez **propriétés obligatoires de l’adaptateur**, puis entrez **chemin d’accès au serveur d’Application**, **JAVA_HOME**, **nom d’utilisateur**,  **mot de passe**et le fichier Jar pour la connexion au système Peoplesoft.</span><span class="sxs-lookup"><span data-stu-id="3815d-115">Expand **Adapter Required Properties**, and enter **Application Server Path**, **JAVA_HOME**, **user name**, **password**, and the Jar file for connecting into the Peoplesoft system.</span></span>  
  
         <span data-ttu-id="3815d-116">Il n'est pas nécessaire de définir les informations de connexion.</span><span class="sxs-lookup"><span data-stu-id="3815d-116">You do not have to set the logon information.</span></span>  
  
    2.  <span data-ttu-id="3815d-117">Dans la liste, sélectionnez l'application associée SSO que vous avez créée pour représenter le système PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="3815d-117">In the list, select the SSO affiliate application you created to represent the PeopleSoft system.</span></span>  
  
    3.  <span data-ttu-id="3815d-118">Pour **utiliser SSO**, sélectionnez **Oui**.</span><span class="sxs-lookup"><span data-stu-id="3815d-118">For **Use SSO**, select **Yes**.</span></span>  
  
    4.  <span data-ttu-id="3815d-119">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3815d-119">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="3815d-120">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3815d-120">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3815d-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3815d-121">See Also</span></span>  
 [<span data-ttu-id="3815d-122">Création de gestionnaires d’envoi PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="3815d-122">Creating PeopleSoft Send Handlers</span></span>](../core/creating-peoplesoft-send-handlers.md)