---
title: Erlang - Tips
description: 
published: true
date: 2023-12-01T18:54:42.428Z
tags: 
editor: markdown
dateCreated: 2023-12-01T18:54:42.428Z
---

# Reversing
If debugging information is still present, this gets to pretty good code.

`
└─# erl -noshell -eval '{ok,{_,[{abstract_code,{_,AC}}]}} = beam_lib:chunks("targetfilename.beam",[abstract_code]),io:put_chars(erl_prettypr:format(erl_syntax:form_list(AC))), halt().' > targetfilename.erl
`

This will decompile all .beam files in find results
`find . -type f -name "*.beam" -exec sh -c 'erl -noshell -eval "{ok,{_,[{abstract_code,{_,AC}}]}} = beam_lib:chunks(\"{}\",[abstract_code]),io:put_chars(erl_prettypr:format(erl_syntax:form_list(AC))), halt()." > {}.erl' \;`


If no debugging present this might work:
`erl -noshell -eval "erlang:display(beam_disasm:file(web_controller_assets))." -eval ' init:stop(). ' > web_controller_assets.S
`