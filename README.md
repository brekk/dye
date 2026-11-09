# dye

A library for manipulating color

[![Madlib Project Badge](https://img.shields.io/badge/madlib-purple?logo=github&logoSize=auto)](//github.com/madlib-lang/madlib) <!-- $MADLIB.projectBadge -->
[![dye v0.0.12](https://img.shields.io/badge/v0.0.12-purple?label=version)](//github.com/brekk/dye) <!-- $MADLIB.json.version -->

---

Dye has some useful algorithms for contrast, luminosity, inverting and generally manipulating color.

```madlib
import Float from "Float"
import IO from "IO"

import Dye from "@/Dye"



main = () => {
  // convert colors to other formats

  pipe(
    Dye.fromHexString,
    IO.pTrace("The separate color channels:"),
  )("#010203")

  // #[1, 35, 69]
  pipe(
    Dye.fromFloat,
    IO.pTrace("The separate color channels, but from a floating point number:"),
  )(0x010203)
  // #[1, 35, 69]

  pipe(
    Dye.bwContrastHex,
    IO.pTrace("highest contrast color, black or white?"),
  )("#4940de")
  // #ffffff

  pipe(
    Dye.fromHexString,
    Dye.change(Float.fromInteger),
    Dye.highContrast(false, $, Dye.WHITE),
    IO.pTrace("was the previous message a lie?"),
  )("#4940de")
  // false
}

