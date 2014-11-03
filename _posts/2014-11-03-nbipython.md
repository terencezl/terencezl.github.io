---
layout: post
title: "nbipython"
tags: python
---
**In [9]:**

{% highlight python linenos %}
Pb=[-88112.3195,
-88112.7909,
-88113.2393,
-88113.6560,
-88114.0470,
-88114.4298,
-88114.7706,]

I = [-32968.2494,
-32968.5714,
-32968.8723,
-32969.1582,
-32969.4122,
-32969.6387,
-32969.8547,]
{% endhighlight %}

**In [2]:**

{% highlight python linenos %}
df= pd.DataFrame(np.array([Pb, I]).T, columns=['Pb','I'])
{% endhighlight %}

**In [10]:**

{% highlight python linenos %}
df.plot(subplots=True,sharex=True)
{% endhighlight %}




    array([<matplotlib.axes._subplots.AxesSubplot object at 0x10e262a10>,
           <matplotlib.axes._subplots.AxesSubplot object at 0x10e2f3210>], dtype=object)



**In [7]:**

{% highlight python linenos %}
Pb[-1] - Pb[0]
{% endhighlight %}




    -2.451100000005681



**In [8]:**

{% highlight python linenos %}
I[-1] - I[0]
{% endhighlight %}




    -1.6053000000028987



**In [12]:**

{% highlight python linenos %}
plt.text(1,-2.5, "difference -2.45")
{% endhighlight %}




    <matplotlib.text.Text at 0x10ec79090>



**In [15]:**

{% highlight python linenos %}
plt.draw()
{% endhighlight %}

**In [14]:**

{% highlight python linenos %}
plt.tight_layout()
{% endhighlight %}

{% highlight python linenos %}
print "12312"
{% endhighlight %}

{% highlight bash linenos %}
echo asdf
{% endhighlight %}

**In [3]:**

{% highlight python linenos %}
plt.plot([231,342])
{% endhighlight %}




    [<matplotlib.lines.Line2D at 0x10dc23250>]



**In [1]:**

{% highlight python linenos %}
plt.rcParams
{% endhighlight %}




    RcParams({u'agg.path.chunksize': 0,
              u'animation.avconv_args': u'',
              u'animation.avconv_path': u'avconv',
              u'animation.bitrate': -1,
              u'animation.codec': u'mpeg4',
              u'animation.convert_args': u'',
              u'animation.convert_path': u'convert',
              u'animation.ffmpeg_args': u'',
              u'animation.ffmpeg_path': u'ffmpeg',
              u'animation.frame_format': u'png',
              u'animation.mencoder_args': u'',
              u'animation.mencoder_path': u'mencoder',
              u'animation.writer': u'ffmpeg',
              u'axes.axisbelow': True,
              u'axes.color_cycle': [u'#E24A33',
                                    u'#348ABD',
                                    u'#988ED5',
                                    u'#777777',
                                    u'#FBC15E',
                                    u'#8EBA42',
                                    u'#FFB5B8'],
              u'axes.edgecolor': u'white',
              u'axes.facecolor': u'#E5E5E5',
              u'axes.formatter.limits': [-7, 7],
              u'axes.formatter.use_locale': False,
              u'axes.formatter.use_mathtext': False,
              u'axes.formatter.useoffset': True,
              u'axes.grid': True,
              u'axes.grid.which': u'major',
              u'axes.hold': True,
              u'axes.labelcolor': u'#555555',
              u'axes.labelsize': u'large',
              u'axes.labelweight': u'normal',
              u'axes.linewidth': 1.0,
              u'axes.titlesize': u'x-large',
              u'axes.titleweight': u'normal',
              u'axes.unicode_minus': True,
              u'axes.xmargin': 0,
              u'axes.ymargin': 0,
              u'axes3d.grid': True,
              u'backend': u'TkAgg',
              u'backend.qt4': u'PyQt4',
              u'backend.qt5': u'PyQt5',
              u'backend_fallback': True,
              u'contour.negative_linestyle': u'dashed',
              u'datapath': u'/Applications/anaconda/lib/python2.7/site-packages/matplotlib/mpl-data',
              u'docstring.hardcopy': False,
              u'examples.directory': u'',
              u'figure.autolayout': False,
              u'figure.dpi': 120.0,
              u'figure.edgecolor': u'0.50',
              u'figure.facecolor': u'white',
              u'figure.figsize': [5.5, 4.0],
              u'figure.frameon': True,
              u'figure.max_open_warning': 20,
              u'figure.subplot.bottom': 0.1,
              u'figure.subplot.hspace': 0.2,
              u'figure.subplot.left': 0.125,
              u'figure.subplot.right': 0.9,
              u'figure.subplot.top': 0.9,
              u'figure.subplot.wspace': 0.2,
              u'font.cursive': [u'Apple Chancery',
                                u'Textile',
                                u'Zapf Chancery',
                                u'Sand',
                                u'cursive'],
              u'font.family': u'sans-serif',
              u'font.fantasy': [u'Comic Sans MS',
                                u'Chicago',
                                u'Charcoal',
                                u'ImpactWestern',
                                u'fantasy'],
              u'font.monospace': [u'Bitstream Vera Sans Mono',
                                  u'DejaVu Sans Mono',
                                  u'Andale Mono',
                                  u'Nimbus Mono L',
                                  u'Courier New',
                                  u'Courier',
                                  u'Fixed',
                                  u'Terminal',
                                  u'monospace'],
              u'font.sans-serif': [u'Bitstream Vera Sans',
                                   u'DejaVu Sans',
                                   u'Lucida Grande',
                                   u'Verdana',
                                   u'Geneva',
                                   u'Lucid',
                                   u'Arial',
                                   u'Helvetica',
                                   u'Avant Garde',
                                   u'sans-serif'],
              u'font.serif': [u'Bitstream Vera Serif',
                              u'DejaVu Serif',
                              u'New Century Schoolbook',
                              u'Century Schoolbook L',
                              u'Utopia',
                              u'ITC Bookman',
                              u'Bookman',
                              u'Nimbus Roman No9 L',
                              u'Times New Roman',
                              u'Times',
                              u'Palatino',
                              u'Charter',
                              u'serif'],
              u'font.size': 10.0,
              u'font.stretch': u'normal',
              u'font.style': u'normal',
              u'font.variant': u'normal',
              u'font.weight': u'normal',
              u'grid.alpha': 1.0,
              u'grid.color': u'white',
              u'grid.linestyle': u'-',
              u'grid.linewidth': 0.5,
              u'image.aspect': u'equal',
              u'image.cmap': u'jet',
              u'image.interpolation': u'bilinear',
              u'image.lut': 256,
              u'image.origin': u'upper',
              u'image.resample': False,
              u'interactive': True,
              u'keymap.all_axes': u'a',
              u'keymap.back': [u'left', u'c', u'backspace'],
              u'keymap.forward': [u'right', u'v'],
              u'keymap.fullscreen': (u'f', u'ctrl+f'),
              u'keymap.grid': u'g',
              u'keymap.home': [u'h', u'r', u'home'],
              u'keymap.pan': u'p',
              u'keymap.quit': (u'ctrl+w', u'cmd+w'),
              u'keymap.save': (u's', u'ctrl+s'),
              u'keymap.xscale': [u'k', u'L'],
              u'keymap.yscale': u'l',
              u'keymap.zoom': u'o',
              u'legend.borderaxespad': 0.5,
              u'legend.borderpad': 0.4,
              u'legend.columnspacing': 2.0,
              u'legend.fancybox': False,
              u'legend.fontsize': u'large',
              u'legend.frameon': True,
              u'legend.handleheight': 0.7,
              u'legend.handlelength': 2.0,
              u'legend.handletextpad': 0.8,
              u'legend.isaxes': True,
              u'legend.labelspacing': 0.5,
              u'legend.loc': u'upper right',
              u'legend.markerscale': 1.0,
              u'legend.numpoints': 2,
              u'legend.scatterpoints': 3,
              u'legend.shadow': False,
              u'lines.antialiased': True,
              u'lines.color': u'b',
              u'lines.dash_capstyle': u'butt',
              u'lines.dash_joinstyle': u'round',
              u'lines.linestyle': u'-',
              u'lines.linewidth': 1.0,
              u'lines.marker': u'None',
              u'lines.markeredgewidth': 0.5,
              u'lines.markersize': 6,
              u'lines.solid_capstyle': u'projecting',
              u'lines.solid_joinstyle': u'round',
              u'mathtext.bf': u'serif:bold',
              u'mathtext.cal': u'cursive',
              u'mathtext.default': u'it',
              u'mathtext.fallback_to_cm': True,
              u'mathtext.fontset': u'cm',
              u'mathtext.it': u'serif:italic',
              u'mathtext.rm': u'serif',
              u'mathtext.sf': u'sans\\-serif',
              u'mathtext.tt': u'monospace',
              u'patch.antialiased': True,
              u'patch.edgecolor': u'#EEEEEE',
              u'patch.facecolor': u'#348ABD',
              u'patch.linewidth': 0.5,
              u'path.effects': [],
              u'path.simplify': True,
              u'path.simplify_threshold': 0.1111111111111111,
              u'path.sketch': None,
              u'path.snap': True,
              u'pdf.compression': 6,
              u'pdf.fonttype': 3,
              u'pdf.inheritcolor': False,
              u'pdf.use14corefonts': False,
              u'pgf.debug': False,
              u'pgf.preamble': [u''],
              u'pgf.rcfonts': True,
              u'pgf.texsystem': u'xelatex',
              u'plugins.directory': u'.matplotlib_plugins',
              u'polaraxes.grid': True,
              u'ps.distiller.res': 6000,
              u'ps.fonttype': 3,
              u'ps.papersize': u'letter',
              u'ps.useafm': False,
              u'ps.usedistiller': False,
              u'savefig.bbox': None,
              u'savefig.directory': u'~',
              u'savefig.dpi': 200.0,
              u'savefig.edgecolor': u'w',
              u'savefig.extension': u'png',
              u'savefig.facecolor': u'w',
              u'savefig.format': u'png',
              u'savefig.frameon': True,
              u'savefig.jpeg_quality': 95,
              u'savefig.orientation': u'portrait',
              u'savefig.pad_inches': 0.1,
              u'savefig.transparent': False,
              u'svg.embed_char_paths': True,
              u'svg.fonttype': u'path',
              u'svg.image_inline': True,
              u'svg.image_noscale': False,
              u'text.antialiased': True,
              u'text.color': u'k',
              u'text.dvipnghack': None,
              u'text.hinting': True,
              u'text.hinting_factor': 8,
              u'text.latex.preamble': [u''],
              u'text.latex.preview': False,
              u'text.latex.unicode': False,
              u'text.usetex': False,
              u'timezone': u'UTC',
              u'tk.pythoninspect': False,
              u'tk.window_focus': False,
              u'toolbar': u'toolbar2',
              u'verbose.fileo': u'sys.stdout',
              u'verbose.level': u'silent',
              u'webagg.open_in_browser': True,
              u'webagg.port': 8988,
              u'webagg.port_retries': 50,
              u'xtick.color': u'#555555',
              u'xtick.direction': u'out',
              u'xtick.labelsize': u'medium',
              u'xtick.major.pad': 4,
              u'xtick.major.size': 4,
              u'xtick.major.width': 0.5,
              u'xtick.minor.pad': 4,
              u'xtick.minor.size': 2,
              u'xtick.minor.width': 0.5,
              u'ytick.color': u'#555555',
              u'ytick.direction': u'out',
              u'ytick.labelsize': u'medium',
              u'ytick.major.pad': 4,
              u'ytick.major.size': 4,
              u'ytick.major.width': 0.5,
              u'ytick.minor.pad': 4,
              u'ytick.minor.size': 2,
              u'ytick.minor.width': 0.5})



**In [2]:**

{% highlight python linenos %}
plt.rcParams['figure.dpi'] = 50
{% endhighlight %}

**In [1]:**

{% highlight python linenos %}
mpl.get_backend()
{% endhighlight %}




    u'MacOSX'



**In []:**

{% highlight python linenos %}

{% endhighlight %}
