# resources

Διάφορες σημειώσεις που μπορεί να φανούν χρήσιμες.  

Με το Notepad++>Search>Find in Files...>Find what:>Directory:>Find All μπορείς να δώσεις ένα κείμενο και ένα directory και να ψάξει όλα τα subdirectories για το συγκεκριμένο κείμενο.

#### ..\duelyst-main\app\data\resources.js  
Εδώ φαίνεται ότι δημιουργεί πληροφορίες για τα resources ώστε όταν αναφέρει π.χ. f2PandaBearAttack να ξέρει σε ποιο frame αναφέρεται και άλλες πληροφορίες όπως το frameDelay, αλλά κι ότι το sfx_f1_general_hit είναι ο ήχος sfx_f1_general_hit.m4a.
```
  sfx_f1_general_attack_impact: { name: 'sfx_f1_general_attack_impact', audio: 'resources/sfx/sfx_f1_general_attack_impact.m4a' },
  sfx_f1_general_attack_swing: { name: 'sfx_f1_general_attack_swing', audio: 'resources/sfx/sfx_f1_general_attack_swing.m4a' },
  sfx_f1_general_hit: { name: 'sfx_f1_general_hit', audio: 'resources/sfx/sfx_f1_general_hit.m4a' },
  ...
  f2PandaBearAttack: {
    name: 'f2PandaBearAttack', img: 'resources/units/f2_pandabear02.png', is16Bit: true, plist: 'resources/units/f2_pandabear02.plist', framePrefix: 'f2_pandabear02_attack_', frameDelay: 0.08,
  },
  f2PandaBearBreathing: {
    name: 'f2PandaBearBreathing', img: 'resources/units/f2_pandabear02.png', is16Bit: true, plist: 'resources/units/f2_pandabear02.plist', framePrefix: 'f2_pandabear02_breathing_', frameDelay: 0.14,
  },
```

#### ..\duelyst-main\app\common\utils\utils_resources.js
Εδώ φαίνεται ότι προσπαθεί να αντλήσει πληροφορία από το object resources
```
/**
 * Returns a list of resource paths from a list of resource data objects.
 * @param {Array} resources
 * @return {Array}
 */
UtilsResources.getResourcePathsFromResources = function (resources) {
  let resourcePaths = [];
  for (let i = 0, il = resources.length; i < il; i++) {
    const resource = resources[i];
    if (resource.img != null) { resourcePaths.push(resource.img); }
    if (resource.plist != null) { resourcePaths.push(resource.plist); }
    if (resource.audio != null) { resourcePaths.push(resource.audio); }
    if (resource.font != null) { resourcePaths.push(resource.font); }
  }
  resourcePaths = _.uniq(resourcePaths);
  return resourcePaths;
};
```
