
> ## เอาของเข้าตู้เซฟ
1. ให้ไปที่ `renzer_Vault\config` จากนั้นเปิดไฟล์ `config.function.lua`
2. มองหา Function `RZ.ServerPutItemVault` นำโค้ดต่อไปนี้ ไปวางใน Function
```lua
if item.type == 'item' then
        local sendToDiscord = '' .. xPlayer.name .. ' ฝาก ' .. ESX.GetItemLabel(item.name) .. ' จำนวน ' .. ESX.Math.GroupDigits(item.number) .. ' ชิ้น เข้าตู้นิรภัย'
        if vault == 'vault' then
            TriggerEvent('azael_dc-serverlogs:sendToDiscord', 'VaultPutItem', sendToDiscord, source, '^2')
        elseif vault == 'police' then
            TriggerEvent('azael_dc-serverlogs:sendToDiscord', 'VaultPutItemPolice', sendToDiscord, source, '^2')
        elseif vault == 'ambulance' then
            TriggerEvent('azael_dc-serverlogs:sendToDiscord', 'VaultPutItemAmbulance', sendToDiscord, source, '^2')
        elseif vault == 'mechanic' then
            TriggerEvent('azael_dc-serverlogs:sendToDiscord', 'VaultPutItemMechanic', sendToDiscord, source, '^2')
        elseif vault == 'council' then
            TriggerEvent('azael_dc-serverlogs:sendToDiscord', 'VaultPutItemCouncil', sendToDiscord, source, '^2')
        end

    elseif item.type == 'account' then
        local sendToDiscord = '' .. xPlayer.name .. ' ฝาก Derty Money จำนวน $' .. ESX.Math.GroupDigits(item.number) .. ' เข้าตู้นิรภัย'
        if vault == 'vault' then
            TriggerEvent('azael_dc-serverlogs:sendToDiscord', 'VaultPutMoney', sendToDiscord, source, '^3')
        elseif vault == 'police' then
            TriggerEvent('azael_dc-serverlogs:sendToDiscord', 'VaultPutMoneyPolice', sendToDiscord, source, '^3')
        elseif vault == 'council' then
            TriggerEvent('azael_dc-serverlogs:sendToDiscord', 'VaultPutMoneyCouncil', sendToDiscord, source, '^3')
        end
    elseif item.type == 'weapon' then
        local sendToDiscord
        if weaponAmmo ~= nil and weaponAmmo > 1 then
            sendToDiscord = '' .. xPlayer.name .. ' ฝาก ' .. ESX.GetWeaponLabel(item.name) .. ' และ กระสุน จำนวน ' .. ESX.Math.GroupDigits(weaponAmmo) .. ' เข้าตู้นิรภัย'
        else
            sendToDiscord = '' .. xPlayer.name .. ' ฝาก ' .. ESX.GetWeaponLabel(item.name) .. ' เข้าตู้นิรภัย'
        end
        if vault == 'vault' then
            TriggerEvent('azael_dc-serverlogs:sendToDiscord', 'VaultPutWeapon', sendToDiscord, source, '^3')
        elseif vault == 'police' then
            TriggerEvent('azael_dc-serverlogs:sendToDiscord', 'VaultPutWeaponPolice', sendToDiscord, source, '^2')
        elseif vault == 'ambulance' then
            TriggerEvent('azael_dc-serverlogs:sendToDiscord', 'VaultPutWeaponAmbulance', sendToDiscord, source, '^2')
        elseif vault == 'mechanic' then
            TriggerEvent('azael_dc-serverlogs:sendToDiscord', 'VaultPutWeaponMechanic', sendToDiscord, source, '^2')
        elseif vault == 'council' then
            TriggerEvent('azael_dc-serverlogs:sendToDiscord', 'VaultPutWeaponCouncil', sendToDiscord, source, '^2')
        end
    end
```
3. อย่าลืมนำ Event Name ไปเพิ่มใน config ของ สคริป azael_dc-serverlogs ด้วย

> ## เอาของออกจากตู้เซฟ
1. ให้ไปที่ `renzer_Vault\config` จากนั้นเปิดไฟล์ `config.function.lua`
2. มองหา Function `RZ.ServerTakeItemVault` นำโค้ดต่อไปนี้ ไปวางใน Function
```lua
if item.type == 'item' then
        local sendToDiscord = '' .. xPlayer.name .. ' นำ ' .. ESX.GetItemLabel(item.name) .. ' จำนวน ' .. ESX.Math.GroupDigits(item.number) .. ' ชิ้น  ออกจากตู้นิรภัย'
        if vault == 'vault' then
            TriggerEvent('azael_dc-serverlogs:sendToDiscord', 'VaultGetItem', sendToDiscord, source, '^1')
        elseif vault == 'police' then
            TriggerEvent('azael_dc-serverlogs:sendToDiscord', 'VaultGetItemJobPolice', sendToDiscord, source, '^1')
        elseif vault == 'ambulance' then
            TriggerEvent('azael_dc-serverlogs:sendToDiscord', 'VaultGetItemJobAmbulance', sendToDiscord, source, '^1')
        elseif vault == 'mechanic' then
            TriggerEvent('azael_dc-serverlogs:sendToDiscord', 'VaultGetItemJobMechanic', sendToDiscord, source, '^1')
        elseif vault == 'council' then
            TriggerEvent('azael_dc-serverlogs:sendToDiscord', 'VaultGetItemJobCouncil', sendToDiscord, source, '^1')
        end

    elseif item.type == 'account' then
        local sendToDiscord = '' .. xPlayer.name .. ' นำ Derty Money จำนวน $' .. ESX.Math.GroupDigits(item.number) .. ' ออกจากตู้นิรภัย'
        if vault == 'vault' then
            TriggerEvent('azael_dc-serverlogs:sendToDiscord', 'VaultGetMoney', sendToDiscord, source, '^1')
        elseif vault == 'police' then
            TriggerEvent('azael_dc-serverlogs:sendToDiscord', 'VaultGetMoneyPolice', sendToDiscord, source, '^1')
        elseif vault == 'council' then
            TriggerEvent('azael_dc-serverlogs:sendToDiscord', 'VaultGetMoneyCouncil', sendToDiscord, source, '^1')
        end
    elseif item.type == 'weapon' then
        local sendToDiscord
        if weaponAmmo ~= nil and weaponAmmo > 1 then
            sendToDiscord = '' .. xPlayer.name .. ' นำ ' .. ESX.GetWeaponLabel(item.name) .. ' และ กระสุน จำนวน ' .. ESX.Math.GroupDigits(weaponAmmo) .. ' ออกจากตู้นิรภัย'
        else
            sendToDiscord = '' .. xPlayer.name .. ' นำ ' .. ESX.GetWeaponLabel(item.name) .. ' ออกจากตู้นิรภัย'
        end
        if vault == 'vault' then
            TriggerEvent('azael_dc-serverlogs:sendToDiscord', 'VaultGetWeapon', sendToDiscord, source, '^1')
        elseif vault == 'police' then
            TriggerEvent('azael_dc-serverlogs:sendToDiscord', 'VaultGetWeaponPolice', sendToDiscord, source, '^1')
        elseif vault == 'ambulance' then
            TriggerEvent('azael_dc-serverlogs:sendToDiscord', 'VaultGetWeaponAmbulance', sendToDiscord, source, '^1')
        elseif vault == 'mechanic' then
            TriggerEvent('azael_dc-serverlogs:sendToDiscord', 'VaultGetWeaponMechanic', sendToDiscord, source, '^1')
        elseif vault == 'council' then
            TriggerEvent('azael_dc-serverlogs:sendToDiscord', 'VaultGetWeaponCouncil', sendToDiscord, source, '^1')
        end
    end
```
