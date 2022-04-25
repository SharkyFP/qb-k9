# Police K9 Scripts originally forked from FjamZoo https://github.com/FjamZoo/qb-k9

# Use

Press K to show K9 Commands (Both of these are now keymaps so its a on user basis)

# Searching

 You must be facing your target (vehicle or player) when selecting the Search Action, except for Search Area.
 Sometimes the Search Person will pick up the dog. Best to have the dog behind you.

# K9 Spawn Location

458.95 -1016.99 28.17

# You must add this to QB Inventory Server main.lua.
```
    local function HasItem(list, item)

        for i = 1, #list do

            if item == list[i] then
                return true
            end
        end

        return false
    end

    AddEventHandler("inventory:server:SearchLocalVehicleInventory", function(plate, list, cb)
    local trunk = Trunks[plate]
    local glovebox = Gloveboxes[plate]
    local result = false

    if trunk ~= nil then
        for k, v in pairs(trunk.items) do
            local ITEM = trunk.items[k].name
            if HasItem(list, ITEM) then
                RESULT = true
            end
        end
    else
        trunk = GetOwnedVehicleItems(plate)

        for k, v in pairs(TRUNK) do

            local ITEM = TRUNK[k].name
            if HasItem(list, ITEM) then
                RESULT = true
            end
        end

    end

    if glovebox ~= nil then
        for k, v in pairs(glovebox.items) do

            local ITEM = glovebox.items[k].name
            if HasItem(list, ITEM) then
                RESULT = true
            end
        end
    else
        glovebox = GetOwnedVehicleGloveboxItems(plate)

        for k, v in pairs(glovebox) do
            local ITEM = glovebox[k].name
            if HasItem(list, ITEM) then
                RESULT = true
            end
        end
    end
    cb(RESULT)
end)
```
