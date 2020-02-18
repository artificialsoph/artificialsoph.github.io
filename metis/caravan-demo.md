
<script src="//dqeditor.dataquest.io/dq_post_box.js"></script>
  <iframe name="dq_editor" width="100%" height=700 src="//dqeditor.dataquest.io/" style="border: none" >
    <pre id="code">
      x = True
      count = 5
      if x:
        for count in range(count):
          print(count)
    </pre>
    <pre id="hint">
      # markdown here

      * List
      * List 2

      ` code('example') `
    </pre>
    <pre id="answer-code" check-vars="dates, df" check-stdout>
      import pandas as pd
      import numpy as np
      dates = pd.date_range('20130101', periods=6)
      df = pd.DataFrame(np.random.randn(6,3), index=dates, columns=list('ABCD'))
    </pre>
  </iframe>
