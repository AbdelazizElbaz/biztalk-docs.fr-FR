---
title: "Configuration des Options d’alerte de file d’attente et des Notifications | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f78afbf9-6e27-4887-8424-f265fbd8448a
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 914af88b989c73444e16acedf43b9a236897859d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-alert-queue-options-and-notifications"></a><span data-ttu-id="7980c-102">Configuration des Notifications et des Options d’alerte de file d’attente</span><span class="sxs-lookup"><span data-stu-id="7980c-102">Configuring Alert Queue Options and Notifications</span></span>
<span data-ttu-id="7980c-103">Le portail de gestion ESB utilise le Service d’alerte ESB pour générer des alertes comme messages d’erreur arrivent sur le portail et elle utilise le Service de Notification ESB à la file d’attente et envoyer des notifications aux utilisateurs qui s’abonnent aux alertes.</span><span class="sxs-lookup"><span data-stu-id="7980c-103">The ESB Management Portal uses the ESB Alert Service to generate alerts as fault messages arrive at the portal, and it uses the ESB Notification Service to queue and send alert notifications to users that subscribe to alerts.</span></span> <span data-ttu-id="7980c-104">Vous pouvez modifier les paramètres utilisés par ces services dans le portail de gestion ESB.</span><span class="sxs-lookup"><span data-stu-id="7980c-104">You can edit the settings used by these services in the ESB Management Portal.</span></span>  
  
### <a name="to-configure-the-settings-for-the-esb-alert-service"></a><span data-ttu-id="7980c-105">Pour configurer les paramètres pour le Service d’alerte ESB</span><span class="sxs-lookup"><span data-stu-id="7980c-105">To configure the settings for the ESB Alert Service</span></span>  
  
1.  <span data-ttu-id="7980c-106">Veillez à vous connecter au portail à l’aide d’un compte qui est membre du groupe Administrateurs de Microsoft BizTalk Server compte (dont les administrateurs du portail sont automatiquement un membre).</span><span class="sxs-lookup"><span data-stu-id="7980c-106">Ensure that you log on to the portal using an account that is a member of the Microsoft BizTalk Server Administrators account group (of which portal administrators are automatically a member).</span></span>  
  
2.  <span data-ttu-id="7980c-107">Pointez sur le **Admin** onglet dans le menu principal de portail, puis cliquez sur **erreur paramètres** pour ouvrir le portail [Page de paramètres d’erreur](../esb-toolkit/fault-settings-page.md).</span><span class="sxs-lookup"><span data-stu-id="7980c-107">Point to the **Admin** tab on the portal main menu, and then click **Fault Settings** to open the portal [Fault Settings Page](../esb-toolkit/fault-settings-page.md).</span></span>  
  
3.  <span data-ttu-id="7980c-108">Dans le **Options d’alerte pour file d’attente** section, activez ou désactivez le **activer le Service de file d’attente alerte** case à cocher pour activer ou désactiver le service.</span><span class="sxs-lookup"><span data-stu-id="7980c-108">In the **Alert Queue Options** section, select or clear the **Enable Alert Queue Service** check box to enable or disable the service.</span></span>  
  
4.  <span data-ttu-id="7980c-109">Si vous activez le service, modifiez les valeurs dans les autres contrôles pour répondre à nos besoins.</span><span class="sxs-lookup"><span data-stu-id="7980c-109">If you enable the service, edit the values in the remaining controls to suit our requirements.</span></span> <span data-ttu-id="7980c-110">Le service interagit avec Microsoft Active Directory, vous devez spécifier la chaîne de connexion LDAP (Lightweight Directory Access Protocol) appropriée.</span><span class="sxs-lookup"><span data-stu-id="7980c-110">The service interacts with Microsoft Active Directory, so you must specify the appropriate LDAP (Lightweight Directory Access Protocol) connection string.</span></span> <span data-ttu-id="7980c-111">Vous pouvez également spécifier la taille de lot de file d’attente et l’intervalle d’interrogation.</span><span class="sxs-lookup"><span data-stu-id="7980c-111">You can also specify the queue batch size and polling interval.</span></span>  
  
5.  <span data-ttu-id="7980c-112">Cliquez sur **enregistrer** pour enregistrer les nouveaux paramètres.</span><span class="sxs-lookup"><span data-stu-id="7980c-112">Click **Save** to save the new settings.</span></span>  
  
### <a name="to-configure-the-settings-for-the-esb-alert-email-notification-service"></a><span data-ttu-id="7980c-113">Pour configurer les paramètres pour le service de Notification des alertes par courrier électronique pour ESB</span><span class="sxs-lookup"><span data-stu-id="7980c-113">To configure the settings for the ESB Alert Email Notification service</span></span>  
  
1.  <span data-ttu-id="7980c-114">Veillez à vous connecter au portail à l’aide d’un compte qui est membre du groupe Administrateurs de BizTalk Server compte (dont les administrateurs du portail sont automatiquement un membre).</span><span class="sxs-lookup"><span data-stu-id="7980c-114">Ensure that you log on to the portal using an account that is a member of the BizTalk Server Administrators account group (of which portal administrators are automatically a member).</span></span>  
  
2.  <span data-ttu-id="7980c-115">Pointez sur le **Admin** onglet dans le menu principal de portail, puis cliquez sur **erreur paramètres** pour ouvrir le portail [Page de paramètres d’erreur](../esb-toolkit/fault-settings-page.md).</span><span class="sxs-lookup"><span data-stu-id="7980c-115">Point to the **Admin** tab on the portal main menu, and then click **Fault Settings** to open the portal [Fault Settings Page](../esb-toolkit/fault-settings-page.md).</span></span>  
  
3.  <span data-ttu-id="7980c-116">Dans le **Options d’alerte par courrier électronique** section, activez ou désactivez le **activer le Service de messagerie alerte** case à cocher pour activer ou désactiver le service.</span><span class="sxs-lookup"><span data-stu-id="7980c-116">In the **Alert Email Options** section, select or clear the **Enable Alert Email Service** check box to enable or disable the service.</span></span>  
  
4.  <span data-ttu-id="7980c-117">Si vous activez le service, modifiez les valeurs dans les autres contrôles pour répondre à nos besoins.</span><span class="sxs-lookup"><span data-stu-id="7980c-117">If you enable the service, edit the values in the remaining controls to suit our requirements.</span></span> <span data-ttu-id="7980c-118">Spécifiez le nom de serveur de messagerie et l’adresse « de », modifier la taille d’intervalle et le lot d’interrogation en fonction des besoins et spécifiez le chemin d’accès aux fichiers de langue Transformations XSLT (Extensible Stylesheet) utilisé par le service.</span><span class="sxs-lookup"><span data-stu-id="7980c-118">Specify the e-mail server name and the "from" address, change the polling interval and batch size as required, and specify the path to Extensible Stylesheet Language Transformations (XSLT) files that the service uses.</span></span>  
  
5.  <span data-ttu-id="7980c-119">Cliquez sur **enregistrer** pour enregistrer les nouveaux paramètres.</span><span class="sxs-lookup"><span data-stu-id="7980c-119">Click **Save** to save the new settings.</span></span>