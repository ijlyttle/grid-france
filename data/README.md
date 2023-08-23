On git, this will be an empty folder (other than this file). 
When the Quarto project is run, this will be the folder used to write parquet files; it will be imported into the Quarto site.

There are two directories predicated on the treatment of timestamps:

  - `standatd` uses "standard" timestamps (ms), including time zone
  - `fake_utc` projects timestamps into UTC

We need `fake_utc` for the time being, until the [`Temporal` object becomes a part of JavaScript](https://github.com/tc39/proposal-temporal). 
In standard browser-based JavaScript, the only two time zones available are UTC and the local timezone for the browser.
D3 and Observable Plot hew closely to standard JavaScript, and offer scaling and formatting functions for UTC.
Other than "offending the mathematical aesthetic", the only drawback of this projection is that there will appear a gap when daylight-saving time begins, and a duplication when it ends.
