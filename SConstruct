# vim: ft=python expandtab
import os
import subprocess
from site_init import GBuilder, Initialize

opts = Variables()
opts.Add(PathVariable('PREFIX', 'Installation prefix', os.path.expanduser('~/FOSS'), PathVariable.PathIsDirCreate))
opts.Add(BoolVariable('DEBUG', 'Build with Debugging information', 0))
opts.Add(PathVariable('PERL', 'Path to the executable perl', r'C:\Perl\bin\perl.exe', PathVariable.PathIsFile))

env = Environment(variables = opts,
                  ENV=os.environ, tools = ['default', GBuilder], PDB = 'libfreetype.pdb')

Initialize(env)

env.Append(CFLAGS=env['DEBUG_CFLAGS'])
env.Append(CPPDEFINES=env['DEBUG_CPPDEFINES'])

#apinames

env_apinames = env.Clone(PDB = 'apiname.pdb')
api_name = env_apinames.Program('apiname', 'src/tools/apinames.c')

env.Append(CPPPATH=['#include'])

env.Append(CPPDEFINES=['_LIB', 'FT2_BUILD_LIBRARY'])
public_dir = 'include/freetype'

srcs = [
#"src/autofit/afangles.c",
#"src/autofit/afcjk.c",
#"src/autofit/afdummy.c",
#"src/autofit/afglobal.c",
#"src/autofit/afhints.c",
#"src/autofit/afindic.c",
#"src/autofit/aflatin.c",
#"src/autofit/aflatin2.c",
#"src/autofit/afloader.c",
#"src/autofit/afmodule.c",
#"src/autofit/afpic.c",
#"src/autofit/afwarp.c",
"src/autofit/autofit.c",
#"src/base/basepic.c",
#"src/base/ftadvanc.c",
#"src/base/ftapi.c",
"src/base/ftbase.c",
"src/base/ftbbox.c",
"src/base/ftbdf.c",
"src/base/ftbitmap.c",
#"src/base/ftcalc.c",
"src/base/ftcid.c",
#"src/base/ftdbgmem.c",
"src/base/ftdebug.c",
"src/base/ftfstype.c",
"src/base/ftgasp.c",
#"src/base/ftgloadr.c",
"src/base/ftglyph.c",
"src/base/ftgxval.c",
"src/base/ftinit.c",
"src/base/ftlcdfil.c",
#"src/base/ftmac.c",
"src/base/ftmm.c",
#"src/base/ftobjs.c",
"src/base/ftotval.c",
#"src/base/ftoutln.c",
"src/base/ftpatent.c",
"src/base/ftpfr.c",
#"src/base/ftpic.c",
#"src/base/ftrfork.c",
#"src/base/ftsnames.c",
#"src/base/ftstream.c",
"src/base/ftstroke.c",
"src/base/ftsynth.c",
"src/base/ftsystem.c",
#"src/base/fttrigon.c",
"src/base/fttype1.c",
#"src/base/ftutil.c",
"src/base/ftwinfnt.c",
"src/base/ftxf86.c",
"src/bdf/bdf.c",
#"src/bdf/bdfdrivr.c",
#"src/bdf/bdflib.c",
"src/cache/ftcache.c",
#"src/cache/ftcbasic.c",
#"src/cache/ftccache.c",
#"src/cache/ftccmap.c",
#"src/cache/ftcglyph.c",
#"src/cache/ftcimage.c",
#"src/cache/ftcmanag.c",
#"src/cache/ftcmru.c",
#"src/cache/ftcsbits.c",
"src/cff/cff.c",
#"src/cff/cffcmap.c",
#"src/cff/cffdrivr.c",
#"src/cff/cffgload.c",
#"src/cff/cffload.c",
#"src/cff/cffobjs.c",
#"src/cff/cffparse.c",
#"src/cff/cffpic.c",
#"src/cid/cidgload.c",
#"src/cid/cidload.c",
#"src/cid/cidobjs.c",
#"src/cid/cidparse.c",
#"src/cid/cidriver.c",
"src/cid/type1cid.c",
"src/gxvalid/gxvalid.c",
#"src/gxvalid/gxvbsln.c",
#"src/gxvalid/gxvcommn.c",
#"src/gxvalid/gxvfeat.c",
#"src/gxvalid/gxvfgen.c",
#"src/gxvalid/gxvjust.c",
#"src/gxvalid/gxvkern.c",
#"src/gxvalid/gxvlcar.c",
#"src/gxvalid/gxvmod.c",
#"src/gxvalid/gxvmort.c",
#"src/gxvalid/gxvmort0.c",
#"src/gxvalid/gxvmort1.c",
#"src/gxvalid/gxvmort2.c",
#"src/gxvalid/gxvmort4.c",
#"src/gxvalid/gxvmort5.c",
#"src/gxvalid/gxvmorx.c",
#"src/gxvalid/gxvmorx0.c",
#"src/gxvalid/gxvmorx1.c",
#"src/gxvalid/gxvmorx2.c",
#"src/gxvalid/gxvmorx4.c",
#"src/gxvalid/gxvmorx5.c",
#"src/gxvalid/gxvopbd.c",
#"src/gxvalid/gxvprop.c",
#"src/gxvalid/gxvtrak.c",
#"src/gzip/adler32.c",
"src/gzip/ftgzip.c",
#"src/gzip/infblock.c",
#"src/gzip/infcodes.c",
#"src/gzip/inflate.c",
#"src/gzip/inftrees.c",
#"src/gzip/infutil.c",
#"src/gzip/zutil.c",
"src/lzw/ftlzw.c",
#"src/lzw/ftzopen.c",
"src/otvalid/otvalid.c",
#"src/otvalid/otvbase.c",
#"src/otvalid/otvcommn.c",
#"src/otvalid/otvgdef.c",
#"src/otvalid/otvgpos.c",
#"src/otvalid/otvgsub.c",
#"src/otvalid/otvjstf.c",
#"src/otvalid/otvmath.c",
#"src/otvalid/otvmod.c",
"src/pcf/pcf.c",
#"src/pcf/pcfdrivr.c",
#"src/pcf/pcfread.c",
#"src/pcf/pcfutil.c",
"src/pfr/pfr.c",
#"src/pfr/pfrcmap.c",
#"src/pfr/pfrdrivr.c",
#"src/pfr/pfrgload.c",
#"src/pfr/pfrload.c",
#"src/pfr/pfrobjs.c",
#"src/pfr/pfrsbit.c",
#"src/psaux/afmparse.c",
"src/psaux/psaux.c",
#"src/psaux/psauxmod.c",
#"src/psaux/psconv.c",
#"src/psaux/psobjs.c",
#"src/psaux/t1cmap.c",
#"src/psaux/t1decode.c",
#"src/pshinter/pshalgo.c",
#"src/pshinter/pshglob.c",
"src/pshinter/pshinter.c",
#"src/pshinter/pshmod.c",
#"src/pshinter/pshpic.c",
#"src/pshinter/pshrec.c",
"src/psnames/psmodule.c",
#"src/psnames/psnames.c",
#"src/psnames/pspic.c",
#"src/raster/ftraster.c",
#"src/raster/ftrend1.c",
"src/raster/raster.c",
#"src/raster/rastpic.c",
#"src/sfnt/sfdriver.c",
"src/sfnt/sfnt.c",
#"src/sfnt/sfntpic.c",
#"src/sfnt/sfobjs.c",
#"src/sfnt/ttbdf.c",
#"src/sfnt/ttcmap.c",
#"src/sfnt/ttkern.c",
#"src/sfnt/ttload.c",
#"src/sfnt/ttmtx.c",
#"src/sfnt/ttpost.c",
#"src/sfnt/ttsbit.c",
#"src/sfnt/ttsbit0.c",
#"src/smooth/ftgrays.c",
#"src/smooth/ftsmooth.c",
#"src/smooth/ftspic.c",
"src/smooth/smooth.c",
#"src/tools/apinames.c",
#"src/tools/test_afm.c",
#"src/tools/test_bbox.c",
#"src/tools/test_trig.c",
"src/truetype/truetype.c",
#"src/truetype/ttdriver.c",
#"src/truetype/ttgload.c",
#"src/truetype/ttgxvar.c",
#"src/truetype/ttinterp.c",
#"src/truetype/ttobjs.c",
#"src/truetype/ttpic.c",
#"src/truetype/ttpload.c",
#"src/type1/t1afm.c",
#"src/type1/t1driver.c",
#"src/type1/t1gload.c",
#"src/type1/t1load.c",
#"src/type1/t1objs.c",
#"src/type1/t1parse.c",
"src/type1/type1.c",
#"src/type42/t42drivr.c",
#"src/type42/t42objs.c",
#"src/type42/t42parse.c",
"src/type42/type42.c",
"src/winfonts/winfnt.c"]

def gen_exports(target, source, env):
    excludes = ['ftmac.h']
    headers = filter(lambda x: reduce(lambda y, z: y and not x.endswith(z), excludes, True), map(str, source))
    print "headers = ",
    print headers
    args = ['apiname.exe', '-w'] + headers
    fo = file(str(target[0]), 'w')
    subprocess.Popen(args, stdout = fo).wait()
    fo.close()

env.Command('libfreetype.def', Glob('include/freetype/*.h'), gen_exports)
env.Depends('libfreetype.def', [api_name, 'SConstruct'])

dll_name = 'libfreetype6' + env['LIB_SUFFIX']
dll_full_name=dll_name + env['SHLIBSUFFIX']
env.Append(CFLAGS = env['DEBUG_CFLAGS'])
dll = env.SharedLibrary(target=[dll_name, 'libfreetype.lib'], source=srcs + ['libfreetype.def'])

env.AddPostAction(dll, 'mt.exe -nologo -manifest ${TARGET}.manifest -outputresource:$TARGET;2')

env['DOT_IN_SUBS'] = {'@VERSION@': '9.16.11',
                      '@prefix@': env['PREFIX'],
                      '@exec_prefix@': '${prefix}/bin',
                      '@libdir@': '${prefix}/lib',
                      '@includedir@': '${prefix}/include'}

env.DotIn('freetype2.pc', 'freetype2.pc.in')
env.Alias('install', env.Install('$PREFIX/include', ['include/ft2build.h']))
env.Alias('install', env.Install('$PREFIX/include/freetype2/freetype', Glob('include/freetype/*.h')))
env.Alias('install', env.Install('$PREFIX/include/freetype2/freetype/config', Glob('include/freetype/config/*.h')))
env.Alias('install', env.Install('$PREFIX/bin', dll_full_name))
env.Alias('install', env.Install('$PREFIX/lib', 'libfreetype.lib'))
env.Alias('install', env.InstallAs('$PREFIX/lib/freetype.lib', 'libfreetype.lib'))
env.Alias('install', env.Install('$PREFIX/lib/pkgconfig', 'freetype2.pc'))

if env['DEBUG']:
	env.Alias('install', env.Install('$PREFIX/pdb', env['PDB']))
