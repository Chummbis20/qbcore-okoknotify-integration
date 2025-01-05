# QBCore okokNotify Integration

This repository provides instructions for replacing the default QBCore notification system with okokNotify in your FiveM server.

## Description

This guide shows you how to integrate okokNotify with QBCore's notification system, replacing the default notifications while maintaining all functionality.

## Installation Steps

1. Navigate to `qb-core/client/functions.lua`
2. Locate the `QBCore.Functions.Notify` function (approximately around line 152)
3. Replace the existing notification function with the following code:

```lua
function QBCore.Functions.Notify(text, textype, length)
    if textype == "primary" then textype = "inform" end
    if type(text) == "table" then
        local ttext = text.text or 'Placeholder'
        local caption = text.caption or 'Placeholder'
        local ttype = textype or 'inform'
        local length = length or 3000
        exports['okokNotify']:Alert("🔔   Notification   🔔", text, length, "info")
    else
        local ttype = textype or 'inform'
        local ttext = text.text or 'Placeholder'
        local length = length or 5000
        exports['okokNotify']:Alert("🔔   Notification   🔔", text, length, "info")
    end
end
```

## Dependencies

- [okokNotify](https://okok.tebex.io/package/4724993)
- [qb-core](https://github.com/qbcore-framework/qb-core)

## Credits

This is an updated version of the original implementation found in [Marshxan's qb-okokNotify](https://github.com/Marshxan/qb-okokNotify).

## License

This project is open source and available under the MIT License.

## Support

If you encounter any issues, please open an issue in this repository.
