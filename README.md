# mineblock-shit-limiter
<img align="right" src="https://media.tenor.com/OrSLtVr_CLYAAAAC/yandere-dev-yandere.gif)/100/100">

**Mineblock Limiter created by ~~braaandon~~ MyMineBlock**

He or She rediculing Bruce for saying he can't code.

Okay buddy let's take a look at **Mineblock Limiter**!

![image](https://user-images.githubusercontent.com/108382118/220800980-22f3410a-0ebf-4d41-bbf5-95422a44535b.png)

**"MyMineBlock" functional component for their netlimiter.**
```using NetLimiter.Service;
using NLMMB.Src;
using System.Windows.Forms;

namespace NLMMB
{
    internal class D2FilterRule
    {
        public string Name;
        private readonly RuleDir _ruleDir;
        private readonly uint _bps;
        private readonly ushort _portStart;
        private readonly ushort _portEnd;
        private readonly NLClient _client;
        private readonly Filter _filt;
        private readonly Rule _rule;
        private readonly Filter _filtModel;
        private readonly Rule _ruleModel;

        public D2FilterRule(NLClient client, string appPath, string name, RuleDir ruleDir, uint bps, ushort portStart = 0, ushort portEnd = 0)
        {
            Name = name;
            _ruleDir = ruleDir;
            _bps = bps;
            _portStart = portStart;
            _portEnd = portEnd;
            _client = client;

            _filtModel = new Filter(Name);
            _filtModel.Functions.Add(new FFAppIdEqual(new AppId(appPath)));
            _filtModel.Functions.Add(new FFRemotePortInRange(new PortRangeFilterValue(_portStart, _portEnd)));
             
            _ruleModel = new LimitRule(_ruleDir, _bps);
            _filt = _client.Filters.Find(x => x.Name == Name);

            if (!Exists())
            {
                _filt = _client.AddFilter(_filtModel);
                _rule = _client.AddRule(_filtModel.Id, _ruleModel);
            }
            else
            {
                _client.RemoveFilter(_filt);
                _filt = _client.AddFilter(_filtModel);
                _rule = _client.AddRule(_filtModel.Id, _ruleModel);
            }

            _rule.IsEnabled = false;
            _client.UpdateRule(_rule);
        }

        public bool Exists()
        {
            return _filt != null;
        }
    }
} 
```
---------------------------------------------------------------

**"Brandon's" functional component for his netlimiter.**
``` using NetLimiter.Service;
using System;
using System.Windows.Forms;

namespace nlsetup
{
    internal class D2Filter
    {
        public string Name;
        public Keys Hotkey;
        public KeyModifiers Modifiers;

        private uint _bps;
        private ushort _portStart;
        private ushort _portEnd;

        private NLClient _client;

        private Filter _filt;
        private Rule _rule;

        private Filter _filtModel;
        private Rule _ruleModel;

        public D2Filter(NLClient client, string appPath, string name, Keys hotkey, KeyModifiers modifiers, uint bps, ushort portStart = 0, ushort portEnd = 0)
        {
            Name = name;
            Hotkey = hotkey;
            Modifiers = modifiers;
            _bps = bps;
            _portStart = portStart;
            _portEnd = portEnd;

            _client = client;

            _filtModel = new Filter(Name);
            _filtModel.Functions.Add(new FFAppIdEqual(new AppId(appPath)));
            if (_portStart > 0 && _portEnd > 0) _filtModel.Functions.Add(new FFRemotePortInRange(new PortRangeFilterValue(_portStart, _portEnd)));

            _ruleModel = new LimitRule(RuleDir.In, _bps);

            _filt = _client.Filters.Find(x => x.Name == Name);

            if (!Exists())
            {
                _filt = _client.AddFilter(_filtModel);
                _rule = _client.AddRule(_filtModel.Id, _ruleModel);
            } else
            {
                _rule = _client.Rules.Find(x => x.FilterId == _filt.Id);
            }

            _rule.IsEnabled = false;
            _client.UpdateRule(_rule);

            if (hotkey != Keys.None)
            {
                HotKeyManager.RegisterHotKey(Hotkey, Modifiers);
                HotKeyManager.HotKeyPressed += new EventHandler<HotKeyEventArgs>((object sender, HotKeyEventArgs e) =>
                {
                    if (e.Key == Hotkey && e.Modifiers == Modifiers)
                    {
                        Toggle();
                    }
                });
            } 
        }

        public bool Exists()
        {
            return _filt != null;
        }

        public bool IsEnabled()
        {
            return _rule.IsEnabled;
        }

        public void Toggle()
        {
            _rule.IsEnabled = !_rule.IsEnabled;
            _client.UpdateRule(_rule);
        }
    }
}
```

## **Nice copy and paste @MyMineBlock**
- I don't know how you did it but you somehow made the stolen code worse?? Takes skill to do that, I'm proud.
- Calls me a skid repeatedly where our functionality is open source and rewritten?
- You also attempt to ridicule my expertise off a dump that was created a month ago in V2, we're in V3.2 now were everything was re-done.
- You then complained that we use VM methods to encrypt our code, tell me the VM we used? Cause there's only methods encryption on Vision, and if you ran Vision through a VM detector, you'd find nothing. But you're a brainless skid that doesn't have the resources to do that.
- On top of that it took you 3 weeks to rename code that wasn't yours and make a UI that sucks?? Sad.

**Only reason why I'm making this post and not leaving him alone**
- Decided to spam distribute malicious files in my discord server when I don't even know this kid nor have I ever spoken to him/her.

**Speaking of your such good coding skills!**

I can't take you seriously when you decided to release a "debug" version of your product to the public.

On top of that your release is literally the source code, do you not know what you're doing?

![image](https://user-images.githubusercontent.com/108382118/220802843-74254c67-4528-4144-b6ba-c68fc161c515.png)
![image](https://user-images.githubusercontent.com/108382118/220802639-4b4f24a1-c41f-46c1-9345-470cc64b969f.png)

**It gets even better...**
- Stolen code? and then when you try to code some things on your own you end up with yandere code and code that is useless. You're so competent man!

**Why are you making FW rules for?**
You're telling people to download netlimiter but then creating FW rules on their pc without them knowing?!
How does Netlimiter and Firewall have anything to do with each other?! 
If you wanted to limit 27k just do it through Netlimiter?? Why do you have to make a FW rule for it?

## Warning, There's no code that actually removes the FW rules he creates, if bungie ever decided to scan firewall rules. All users of this would be flagged and possibly banned in a wave.

![image](https://user-images.githubusercontent.com/108382118/220803211-39bd342f-b908-4ddc-a54b-12cad737bd2f.png)


``` if (checkBox1.Checked)
                {
                    Settings1.Default.hotkeydl3074 = true;
                }
                else
                {
                    Settings1.Default.hotkeydl3074 = false;
                }

                if (checkBox2.Checked)
                {
                    Settings1.Default.hotkeyul3074 = true;
                }
                else
                {
                    Settings1.Default.hotkeyul3074 = false;
                }

                if (checkBox3.Checked)
                {
                    Settings1.Default.hotkeydl7500 = true;
                }
                else
                {
                    Settings1.Default.hotkeydl7500 = false;
                }

                if (checkBox4.Checked)
                {
                    Settings1.Default.hotkeyul7500 = true;
                }
                else
                {
                    Settings1.Default.hotkeyul7500 = false;
                }

                if (checkBox5.Checked)
                {
                    Settings1.Default.hotkeydl27k = true;
                }
                else
                {
                    Settings1.Default.hotkeydl27k = false;
                }

                if (checkBox6.Checked)
                {
                    Settings1.Default.hotkeyul27k = true;
                }
                else
                {
                    Settings1.Default.hotkeyul27k = false;
                }

                if (checkBox7.Checked)
                {
                    Settings1.Default.hotkeylfg = true;
                }
                else
                {
                    Settings1.Default.hotkeylfg = false;
                }

                if (checkBox8.Checked)
                {
                    Settings1.Default.hotkey30kl = true;
                }
                else
                {
                    Settings1.Default.hotkey30kl = false;
                }

                if (checkBox9.Checked)
                {
                    Settings1.Default.hotkey30kkc = true;
                }
                else
                {
                    Settings1.Default.hotkey30kkc = false;
                }

                if (checkBox10.Checked)
                {
                    Settings1.Default.hotkeygp = true;
                }
                else
                {
                    Settings1.Default.hotkeygp = false;
                }

                if (checkBox11.Checked)
                {
                    Settings1.Default.hotkeypvel = true;
                }
                else
                {
                    Settings1.Default.hotkeypvel = false;
                }

                if (checkBox12.Checked)
                {
                    Settings1.Default.hotkeypvpl = true;
                }
                else
                {
                    Settings1.Default.hotkeypvpl = false;
                }

                Settings1.Default.Save();
                MessageBox.Show("Restart the application");
            }
            catch (Exception)
            {
                MessageBox.Show("Some type of syntax error");
            }
        }
```
**if else if else if else if else if else**

**Syntax error???**
- Aren't you checking if a checkbox is enabled? How's that a syntax error?

**What is this dude?**

![image](https://user-images.githubusercontent.com/108382118/220804286-2719eaa7-32f1-46a8-b3cc-4f3a13120c6d.png)

<p align="center">Better open source alternatives, instead of this copy pasta garbage that has no protection on it at all.<p align="center">
<p align="center"> Brandon's Limiter (MyMineBlock stole this so you may as well use it instead) - https://github.com/braaandon/nlsetup<p align="center">
<p align="center"> Bruce's Limiter  - https://github.com/NotBruce/Netlimiter-Alternative<p align="center">


<p align="center">
  <img width="500" height="300" src="https://media.tenor.com/SX5B_1kKYYcAAAAC/akame-akamegakill.gif/460/300">
</p>



