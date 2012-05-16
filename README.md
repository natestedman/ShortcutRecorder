# Setup #

## Getting Shortcut Recorder into your project ##

  * Get every header and source file (currently: SRRecorderControl.h, SRRecorderControl.m, SRRecorderCell.h, SRRecorderCell.m, CTGradient.h, CTGradient.m, SRKeyCodeTransformer.h, SRKeyCodeTransformer.m, SRValidator.h, SRValidator.m, SRCommon.h and SRCommon.m) into your project (be sure to copy the files and include them into the Xcode project).

  * Also get the desirable localizations of ShortcutRecorder.strings into your resources. Do not copy the image files into your resources - they have been made obsolete by recent changes to introduce Resolution Independence.  

## Getting an SRRecorderControl into your window or panel ##

There are two routes to go. There are Interface Builder palettes (for 2.x) and plugins (for 3.x on Mac OS X 10.5) for Shortcut Recorder, which you can use. You can also drag in a custom view (with a height of 22), drag the Shortcut Recorder header files onto the NIB's document window and change the class of the view to SRRecorderControl.

# Making Shortcut Recorder work for you #

Supply a delegate and start listening to the `- (BOOL)shortcutRecorder:(SRRecorderControl *)aRecorder isKeyCode:(signed short)keyCode andFlagsTaken:(unsigned int)flags reason:(NSString **)aReason` and 
`- (void)shortcutRecorder:(SRRecorderControl *)aRecorder keyComboDidChange:(KeyCombo)newKeyCombo` methods. They give you an opportunity to reject inappropriate key combinations and later be notified when a new combination has been picked. SInce you'll so often want to implement key combination filtering or set a hot key or save away the key combination when the key combination changes anyway, Shortcut Recorder forgoes the target-action pattern and only sends updates via the delegate.

Beyond that, there are a number of accessor methods, many of which are self-explanatory. Experiment!
