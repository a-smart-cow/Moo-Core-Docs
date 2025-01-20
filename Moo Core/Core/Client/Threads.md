---
title: Exports
nav_order: 1
parent: Client
layout: home
---

# 📃Threads
<hr>
The Threads.lua file contains the logic to disable certain aspects of the default game and tell the server when the player has fully joined. You can see the entirety of this file here:

```LUA
--| :: Disable certain aspects of the game and tell the server that the player has joined
Citizen.CreateThread(function()
    TriggerServerEvent('Player::OnPlayerFullyJoined')

    Citizen.InvokeNative( 0x4CC5F2FC1332577F, 1058184710 )                                  --| Remove skill cards
    Citizen.InvokeNative( 0x4CC5F2FC1332577F, -66088566 )                                   --| Remove money
    Citizen.InvokeNative(0x4CC5F2FC1332577F ,GetHashKey("HUD_CTX_IN_FAST_TRAVEL_MENU"))     --| Remove reticle

    while true do
        Citizen.Wait(0)

        Citizen.InvokeNative( 0x4CC5F2FC1332577F, 474191950 )               --| Remove minimap
        Citizen.InvokeNative( 0x50C803A4CD5932C5, false )                   --| Remove player cores
        Citizen.InvokeNative( 0xD4EE21B7CC7FD350, false )                   --| Remove horse cores
        Citizen.InvokeNative( 0x4B8F743A4A6D2FF8, true )                    --| Hide the minimap

        --| Remove some controls like jumping from horse to horse
        DisableControlAction(0, 0xE4D2CE1D, true)
        DisableControlAction(0, 0x580C4473, true)
        DisableControlAction(0, 0xCF8A4ECA, true)
        DisableControlAction(0, 0xFF8109D8, true)
        DisableControlAction(0, 0x6E9734E8, true)
        DisableControlAction(0, 0xAC4BD4F1, true)                           --| Weapon wheel!
        DisableControlAction(0, 0xE2B557A3, true)                           --| Emote wheel 
        DisableControlAction(0, 0x4FD1C57B, true)
        DisableControlAction(0, 0x8B3FA65E, true)
        DisableControlAction(0, 0x1C826362, true)
        DisableControlAction(0, 0x41AC83D1, true)                           --| Loot
        DisableControlAction(0, 0x399C6619, true)                           --| Loot 2
        DisableControlAction(0, 0x27D1C284, true)                           --| Loot 3
        DisableControlAction(0, 0x14DB6C5E, true)                           --| Loot Vehicle
        DisableControlAction(0, 0xC23D7B9E, true)                           --| Loot Ammo
        DisableControlAction(0, 0xFF8109D8, true)                           --| Loot Alive Component
    end;
end);
```
