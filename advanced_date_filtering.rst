Advanced Date Filtering
=======================

Enterprise Edition Only
Saiku now supports advanced date filters, allowing you to do dynamic date ranges like Last x Periods, Yesterday, Today etc. To take advantage of these features you need to make some adjustments to your schema so Saiku knows how to apply the filters.

Firstly to use the Last Periods, and quick date selectors, you need to implement the Pentaho defined AnalyzerDateFormat. This format allows us to see how your date dimension is structured on any given level. So for example:
   <Hierarchy name="Time" hasAll="false">
      <Level attribute="Year">
            <Annotations>
                  <Annotation name="AnalyzerDateFormat">[yyyy]</Annotation>
                     </Annotations>
                        </Level>
                           <Level attribute="Quarter">
                                 <Annotations>
                                       <Annotation name="AnalyzerDateFormat">[yyyy].[Qq]</Annotation>
                                          </Annotations>
                                             </Level>
                                                <Level attribute="Month">
                                                      <Annotations>
                                                            <Annotation name="AnalyzerDateFormat">[yyyy].[Qq].[mm]</Annotation>
                                                               </Annotations>
                                                                  </Level>
                                                                  </Hierarchy>
                                                                  <Hierarchy name="Weekly" hasAll="true">
                                                                     <Level attribute="Year">
                                                                           <Annotations>
                                                                                 <Annotation name="AnalyzerDateFormat">[yyyy]</Annotation>
                                                                                    </Annotations>
                                                                                       </Level>
                                                                                          <Level attribute="Week">
                                                                                                <Annotations>
                                                                                                      <Annotation name="AnalyzerDateFormat">[yyyy].[Qq].[ww]</Annotation>
                                                                                                         </Annotations>
                                                                                                            </Level>
                                                                                                               <Level attribute="Day">
                                                                                                                     <Annotations>
                                                                                                                           <Annotation name="AnalyzerDateFormat">[yyyy].[Qq].[ww].[dd]</Annotation>
                                                                                                                              </Annotations>
                                                                                                                                 </Level>
                                                                                                                                 </Hierarchy>

                                                                                                                              As you can see from the above snippet, on each level we declare how the MDX would look if you were to hand write the query but instead of putting dates in we just put the format of the levels in. The query then replaces these annotations with actual dates when the query is run. This means that when you reopen the query a new date is entered and as such, they are dynamic.

                                                                                                                           Secondly we have the Operator date selector which allows us to select from different date ranges which are not dynamic but frequently used. For example between, after, before and does not equal. This part of the dialog is controlled by the SaikuDayFormatString annotation.
                                                                                                                     As you can see in the snippet, we apply this only to a day level. SaikuDateProperty refers to a member property you have defined in your schema which is a date string. yyyy/mm/dd, dd/mm/yyyy etc and the SaikuDayFormatString annotation is the format the dates are in.
                                                                                                                  <Level attribute="Day">
                                                                                                                     <Annotations>
                                                                                                                           <Annotation name="AnalyzerDateFormat">[yyyy].[Qq].[ww].[dd]</Annotation>
                                                                                                                              <Annotation name="SaikuDayFormatString">yyyy/mm/dd</Annotation>
                                                                                                                                 </Annotations>
                                                                                                                                 </Level>
