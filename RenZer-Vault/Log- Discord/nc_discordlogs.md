# นี้เป็นเพียงตัวอย่างการเชื่องLog เท่านั้น หากจะแก้ไขอะไรควรเข้าเรื่องของตัวแปรแต่ละตัว
> ## เอาของเข้าตู้เซฟ
1. ให้ไปที่ `renzer_Vault\config` จากนั้นเปิดไฟล์ `config.function.lua`
2. มองหา Function `RZ.ServerPutItemVault` นำโค้ดต่อไปนี้ ไปวางใน Function
```css
if type == 'item' then
    local sendToDiscord = '' .. xPlayer.name .. ' ฝาก ' .. label .. ' จำนวน ' .. ESX.Math.GroupDigits(count) .. ' ชิ้น เข้าตู้นิรภัย'
    if job == 'vault' then
          exports.nc_discordlogs:Discord({
              webhook = 'VaultPutItem',
              xPlayer = xPlayer,
              title = 'ไอเท็มเข้าตู้เซฟ',
              description = sendToDiscord,
              color = 'ff0000',

          })
    else 
        if xPlayer.job.name == 'police' then
            exports.nc_discordlogs:Discord({
              webhook = 'VaultPutItemPolice',
              xPlayer = xPlayer,
              title = 'ไอเท็มเข้าตู้เซฟหน่วยงาน',
              description = sendToDiscord,
              color = 'ff0000',

          })
        elseif xPlayer.job.name == 'ambulance' then
            exports.nc_discordlogs:Discord({
                webhook = 'VaultPutItemAmbulance',
                xPlayer = xPlayer,
                title = 'ไอเท็มเข้าตู้เซฟหน่วยงาน',
                description = sendToDiscord,
                color = 'ff0000',

            })
        elseif xPlayer.job.name == 'mechanic' then
            exports.nc_discordlogs:Discord({
              webhook = 'VaultPutItemMechanic',
              xPlayer = xPlayer,
              title = 'ไอเท็มเข้าตู้เซฟหน่วยงาน',
              description = sendToDiscord,
              color = 'ff0000',

          })
        elseif xPlayer.job.name == 'council' then
            exports.nc_discordlogs:Discord({
              webhook = 'VaultPutItemCouncil',
              xPlayer = xPlayer,
              title = 'ไอเท็มเข้าตู้เซฟหน่วยงาน',
              description = sendToDiscord,
              color = 'ff0000',

            })
        end
    end
elseif type == 'account' then
    local sendToDiscord = '' .. xPlayer.name .. ' ฝาก Derty Money จำนวน $' .. ESX.Math.GroupDigits(count) .. ' เข้าตู้นิรภัย'
    if job == 'vault' then
		TriggerEvent('azael_dc-serverlogs:sendToDiscord', 'VaultPutMoney', sendToDiscord, source, '^3')
          exports.nc_discordlogs:Discord({
              webhook = 'VaultPutMoney',
              xPlayer = xPlayer,
              title = 'เงินแดงเข้าตู้เซฟ',
              description = sendToDiscord,
              color = 'ff0000',

           })
    else
        if xPlayer.job.name == 'police' then
            exports.nc_discordlogs:Discord({
                webhook = 'VaultPutMoneyPolice',
                xPlayer = xPlayer,
                title = 'เงินแดงเข้าตู้เซฟหน่วยงาน',
                description = sendToDiscord,
                color = 'ff0000',

             })
        elseif xPlayer.job.name == 'council' then
            exports.nc_discordlogs:Discord({
                webhook = 'VaultPutMoneyCouncil',
                xPlayer = xPlayer,
                title = 'เงินแดงเข้าตู้เซฟหน่วยงาน',
                description = sendToDiscord,
                color = 'ff0000',

             })
        end
    end
elseif type == 'weapon' then
    local sendToDiscord
        
    if count ~= nil and count > 1 then
        sendToDiscord = '' .. xPlayer.name .. ' ฝาก ' .. label .. ' และ กระสุน จำนวน ' .. ESX.Math.GroupDigits(count) .. ' เข้าตู้นิรภัย'
    else
        sendToDiscord = '' .. xPlayer.name .. ' ฝาก ' .. label .. ' เข้าตู้นิรภัย'
    end
    if job == 'vault' then
      exports.nc_discordlogs:Discord({
         webhook = 'VaultPutWeapon',
         xPlayer = xPlayer,
         title = 'อาวุธเข้าตู้เซฟ',
         description = sendToDiscord,
         color = 'ff0000',

       })
    else
        if xPlayer.job.name == 'police' then
              exports.nc_discordlogs:Discord({
                 webhook = 'VaultPutWeaponPolice',
                 xPlayer = xPlayer,
                 title = 'อาวุธเข้าตู้เซฟหน่วยงาน',
                 description = sendToDiscord,
                 color = 'ff0000',

               })
        elseif xPlayer.job.name == 'ambulance' then
            exports.nc_discordlogs:Discord({
                 webhook = 'VaultPutWeaponAmbulance',
                 xPlayer = xPlayer,
                 title = 'อาวุธเข้าตู้เซฟหน่วยงาน',
                 description = sendToDiscord,
                 color = 'ff0000',

            })
        elseif xPlayer.job.name == 'mechanic' then
            exports.nc_discordlogs:Discord({
                 webhook = 'VaultPutWeaponMechanic',
                 xPlayer = xPlayer,
                 title = 'อาวุธเข้าตู้เซฟหน่วยงาน',
                 description = sendToDiscord,
                 color = 'ff0000',

            })
        elseif xPlayer.job.name == 'council' then
            exports.nc_discordlogs:Discord({
                 webhook = 'VaultPutWeaponCouncil',
                 xPlayer = xPlayer,
                 title = 'อาวุธเข้าตู้เซฟหน่วยงาน',
                 description = sendToDiscord,
                 color = 'ff0000',

            })
        end
    end
end
```
3. อย่าลืมนำ webhook ไปเพิ่มใน config ของ สคริป nc_discordlogs ด้วย

> ## เอาของออกจากตู้เซฟ
1. ให้ไปที่ `renzer_Vault\config` จากนั้นเปิดไฟล์ `config.function.lua`
2. มองหา Function `RZ.ServerTakeItemVault` นำโค้ดต่อไปนี้ ไปวางใน Function
```css
if type == 'item' then
    local sendToDiscord = '' .. xPlayer.name .. ' นำ ' .. label .. ' จำนวน ' .. ESX.Math.GroupDigits(count) .. ' ชิ้น ออกจากตู้นิรภัย'
    if job == 'vault' then
        exports.nc_discordlogs:Discord({
                 webhook = 'VaultGetItem',
                 xPlayer = xPlayer,
                 title = 'ไอเท็มออกตู้เซฟ',
                 description = sendToDiscord,
                 color = 'ff0000',

         })
    else 
        if xPlayer.job.name == 'police' then
            exports.nc_discordlogs:Discord({
                 webhook = 'VaultGetItemJobPolice',
                 xPlayer = xPlayer,
                 title = 'ไอเท็มออกตู้เซฟหน่วยงาน',
                 description = sendToDiscord,
                 color = 'ff0000',
            })
        elseif xPlayer.job.name == 'ambulance' then
            exports.nc_discordlogs:Discord({
                 webhook = 'VaultGetItemJobAmbulance',
                 xPlayer = xPlayer,
                 title = 'ไอเท็มออกตู้เซฟหน่วยงาน',
                 description = sendToDiscord,
                 color = 'ff0000',
            })
        elseif xPlayer.job.name == 'mechanic' then
            exports.nc_discordlogs:Discord({
                 webhook = 'VaultGetItemJobMechanic',
                 xPlayer = xPlayer,
                 title = 'ไอเท็มออกตู้เซฟหน่วยงาน',
                 description = sendToDiscord,
                 color = 'ff0000',
            })
        elseif xPlayer.job.name == 'council' then
            exports.nc_discordlogs:Discord({
                 webhook = 'VaultGetItemJobCouncil',
                 xPlayer = xPlayer,
                 title = 'ไอเท็มออกตู้เซฟหน่วยงาน',
                 description = sendToDiscord,
                 color = 'ff0000',
            })
        end
    end
elseif type == 'account' then
    local sendToDiscord = '' .. xPlayer.name .. ' นำ Derty Money จำนวน $' .. ESX.Math.GroupDigits(count) .. ' ออกจากตู้นิรภัย'
    if job == 'vault' then
        exports.nc_discordlogs:Discord({
             webhook = 'VaultGetMoney',
             xPlayer = xPlayer,
             title = 'เงินแดงออกตู้เซฟ',
             description = sendToDiscord,
             color = 'ff0000',
        })
    else
        if xPlayer.job.name == 'police' then
            exports.nc_discordlogs:Discord({
               webhook = 'VaultGetMoneyPolice',
               xPlayer = xPlayer,
               title = 'เงินแดงออกตู้เซฟหน่วยงาน',
               description = sendToDiscord,
               color = 'ff0000',
             })
        elseif xPlayer.job.name == 'council' then
            exports.nc_discordlogs:Discord({
               webhook = 'VaultGetMoneyCouncil',
               xPlayer = xPlayer,
               title = 'เงินแดงออกตู้เซฟหน่วยงาน',
               description = sendToDiscord,
               color = 'ff0000',
            })
        end
    end
elseif type == 'weapon' then
    local sendToDiscord
    
    if count ~= nil and count > 1 then
        sendToDiscord = '' .. xPlayer.name .. ' ฝาก ' .. label .. ' และ กระสุน จำนวน ' .. ESX.Math.GroupDigits(count) .. ' ออกจากตู้นิรภัย'
    else
        sendToDiscord = '' .. xPlayer.name .. ' ฝาก ' .. label .. ' ออกจากตู้นิรภัย'
    end
    if job == 'vault' then
        exports.nc_discordlogs:Discord({
               webhook = 'VaultGetWeapon',
               xPlayer = xPlayer,
               title = 'อาวุธออกตู้เซฟ',
               description = sendToDiscord,
               color = 'ff0000',
            })
    else
        if xPlayer.job.name == 'police' then
             exports.nc_discordlogs:Discord({
               webhook = 'VaultGetWeaponPolice',
               xPlayer = xPlayer,
               title = 'อาวุธออกตู้เซฟหน่วยงาน',
               description = sendToDiscord,
               color = 'ff0000',
            })
        elseif xPlayer.job.name == 'ambulance' then
            exports.nc_discordlogs:Discord({
               webhook = 'VaultGetWeaponAmbulance',
               xPlayer = xPlayer,
               title = 'อาวุธออกตู้เซฟหน่วยงาน',
               description = sendToDiscord,
               color = 'ff0000',
            })
        elseif xPlayer.job.name == 'mechanic' then
             exports.nc_discordlogs:Discord({
               webhook = 'VaultGetWeaponMechanic',
               xPlayer = xPlayer,
               title = 'อาวุธออกตู้เซฟหน่วยงาน',
               description = sendToDiscord,
               color = 'ff0000',
            })
        elseif xPlayer.job.name == 'council' then
             exports.nc_discordlogs:Discord({
               webhook = 'VaultGetWeaponCouncil',
               xPlayer = xPlayer,
               title = 'อาวุธออกตู้เซฟหน่วยงาน',
               description = sendToDiscord,
               color = 'ff0000',
            })
        end
    end
end
```
3. อย่าลืมนำ webhook ไปเพิ่มใน config ของ สคริป nc_discordlogs ด้วย
