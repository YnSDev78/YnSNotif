# YnSNotif
Notification UI FiveM type FlashBack FA

Mofification ES.EXTENDED : 
es_extended/client/fxmanifest.lua:

function ESX.ShowNotification(msg, couleurProgress)
    exports.notif:Send(msg, couleurProgress)
end


function ESX.ShowAdvancedNotification(title, subject, msg, couleurProgress, banner, timeout, icon)
    exports.notif:SendAdvanced(msg, subject, title, couleurProgress, banner, nil, nil, true, nil, icon)
end

function ESX.ShowHelpNotification(msg)
	AddTextEntry('esxHelpNotification', msg)
	BeginTextCommandDisplayHelp('esxHelpNotification')
	EndTextCommandDisplayHelp(0, false, true, -1)
end

Type de notification : 

client : 
RegisterCommand('2', function()
    ESX.ShowNotification("Le Los Santos Custom est ~g~ouvert", "#5fa05d")
end)

RegisterCommand('3', function()
    ESX.ShowNotification("Le Los Santos Custom est ~r~fermer", "#FF0000")
end)

RegisterCommand('1', function()
	ESX.ShowAdvancedNotification('~p~Appel d\'urgence - 2061', '~p~Central', "~p~Localisation:~s~\n<b><span style='font-weight: 500;'>Groove Street (15m)</span></b>\n~p~Infos:~s~\n<b><span style='font-weight: 500'>Tire à feux</span></b>", '#b19bd9', 'call', 7)
end)

server : 

RegisterCommand('3', function()
    TriggerClientEvent('esx:showNotification', _src, "Le Los Santos Custom est ~r~fermer", "#FF0000")
end)
