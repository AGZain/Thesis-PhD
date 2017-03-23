<!--

```@mermaid
gantt
        dateFormat  YYYY-MM-DD
        title Adding GANTT diagram functionality to mermaid
        section A section
        Completed task            :done,    des1, 2014-01-06,2014-01-08
        Active task               :active,  des2, 2014-01-09, 3d
        Future task               :         des3, after des2, 5d
        Future task2               :         des4, after des3, 5d
        section Critical tasks
        Completed task in the critical line :crit, done, 2014-01-06,24h
        Implement parser and jison          :crit, done, after des1, 2d
        Create tests for parser             :crit, active, 3d
        Future task in critical line        :crit, 5d
        Create tests for renderer           :2d
        Add to mermaid                      :1d

``` -->

```@mermaid
gantt
        dateFormat  YYYY-MM-DD
        title Course of Proposed Work

%        section Learning tasks
%        Study Category Theory             :active, 2017-01-24, 90d
%        Study Functional Programming      :active, 2017-02-12, 90d
%        Study FRP                         :active, 2017-03-09, 90d

        section Design/Construction
        Design of FRP framework            :active, 2017-04-01, 12w
        virtualME Adaptation               :active, 2017-06-01, 6w
        Research Application               :active, 2017-07-07, 6w

        section Authorship
        Thesis writing                     :active, 2017-08-05, 8w

        section PhD Dates
        Proposal                           :crit, 2017-02-13, 1d
        Deadline                           :crit, 2017-06-12, 1d
        Deadline                           :crit, 2017-10-10, 1d
```
