% Transfilytics- Ferramenta para análise de filtros e sistemas de controle (MATLAB version).
%
%   Esta ferramenta permite a entrada de uma função de transferência de três
%   formas distintas:
%   1. Coeficientes do numerador e denominador.
%   2. Zeros, polos e ganho k.
%   3. Expressão simbólica em 's'.
%
%   Funcionalidades Principais:
%   - **Detecção Automática de Filtro:** Classifica o sistema como Passa-Baixas,
%     Passa-Altas, Passa-Banda ou Rejeita-Banda.
%   - **Cálculo de Parâmetros:** Determina as frequências de corte (-3 dB),
%     frequência central, largura de banda e fator de qualidade (Q)
%     conforme o tipo de filtro.
%   - **Visualização Completa:** Gera três gráficos interligados:
%     - Diagrama de Bode (Magnitude) com marcações relevantes.
%     - Diagrama de Bode (Fase).
%     - Plano-s com a localização de zeros e polos.
%   - **Interface Gráfica Moderna:** Utiliza uma interface com tema escuro
%     para melhor visualização e organização das informações.
%   - **Faixa de Frequência Adaptativa:** Ajusta automaticamente o range
%     do diagrama de Bode para focar na região de interesse do sistema.
%
% Requisitos:
%   - MATLAB R2020a ou mais recente.
%   - Control System Toolbox.
%
% Histórico de Melhorias:
%   - **v1.4 (Atual):**
%     - Corrigido o erro de sintaxe "Illegal use of reserved keyword 'end'"
%       reestruturando todas as funções auxiliares para que estejam
%       corretamente aninhadas dentro da função principal.
%   - **v1.3 (Anterior):**
%     - Corrigido o erro "Illegal use of reserved keyword 'end'" corrigindo a
%       estrutura das funções internas para que todas fiquem corretamente
%       aninhadas.
%   - **v1.2 (Anterior):**
%     - Corrigido o erro "Illegal use of reserved keyword 'end'" removendo um
%       'end' extra após a função 'limpar()'.
%   - **v1.1 (Anterior):**
%     - Corrigida a lógica da função 'fitPlaneLimits' para garantir uma
%       proporção 1:1 no gráfico do plano-s.
%     - Ajustada a criação da legenda do plano-s para usar a propriedade
%       'DisplayName', mostrando os marcadores corretos (círculo e x).
function analisador_filtros_v4()
    if ~license('test','Control_Toolbox')
        uialert(uifigure,'É necessário o Control System Toolbox.','Requisito ausente');
        return
    end
    fig = uifigure('Name','Analisador Avançado de Filtros e Sistemas',...
                    'Position',[80 60 1280 820], 'Color',[0.08 0.08 0.1]);
    gl = uigridlayout(fig,[1 2]);
    gl.ColumnWidth = {460,'1x'};

    %% ---- Lado esquerdo (entradas e controles)
    left = uigridlayout(gl,[7 1]);
    left.RowHeight = {120, 165, 95, 100, 40, '1x', 40};
    left.Padding = [8 8 8 8];
    left.BackgroundColor = fig.Color;

    p1 = uipanel(left,'Title','1. Entrada por Coeficientes (Função de Transferência)',...
        'FontWeight','bold','ForegroundColor',[1 1 1],'BackgroundColor',fig.Color);
    g1 = uigridlayout(p1,[4 1]); g1.RowHeight = {20,30,20,30};
    uilabel(g1,'Text','Numerador (ex: [2 4 -6]):','FontColor',[0.9 0.9 0.9]);
    eNum = uieditfield(g1,'text','Value','[1000]');
    uilabel(g1,'Text','Denominador (ex: [1 7 -6 -1]):','FontColor',[0.9 0.9 0.9]);
    eDen = uieditfield(g1,'text','Value','[1 1000]');

    p2 = uipanel(left,'Title','2. Entrada por Zeros, Polos e Ganho',...
        'FontWeight','bold','ForegroundColor',[1 1 1],'BackgroundColor',fig.Color);
    g2 = uigridlayout(p2,[4 2]);
    g2.RowHeight = {20,30,20,30};
    g2.ColumnWidth = {'1x', 80};
    uilabel(g2,'Text','Zeros (ex: [-1 -2j -2+j]):','FontColor',[0.9 0.9 0.9]);
    uilabel(g2,'Text','Ganho (k):','FontColor',[0.9 0.9 0.9]);
    eZ = uieditfield(g2,'text');
    eK = uieditfield(g2,'text','Value','1');
    polos_label = uilabel(g2,'Text','Polos (ex: [-3 -4-5j -4+5j]):','FontColor',[0.9 0.9 0.9]);
    polos_label.Layout.Row = 3;
    polos_label.Layout.Column = [1, 2];
    eP = uieditfield(g2,'text');
    eP.Layout.Row = 4;
    eP.Layout.Column = [1, 2];

    p3 = uipanel(left,'Title','3. Entrada por Expressão Simbólica',...
        'FontWeight','bold','ForegroundColor',[1 1 1],'BackgroundColor',fig.Color);
    g3 = uigridlayout(p3,[2 1]); g3.RowHeight = {20,30};
    uilabel(g3,'Text','Função G(s) (ex: 1000/(s+1000)):', 'FontColor',[0.9 0.9 0.9]);
    eSym = uieditfield(g3,'text');

    pEx = uipanel(left,'Title','Exemplos Rápidos','FontWeight','bold','ForegroundColor',[1 1 1],'BackgroundColor',fig.Color);
    gEx = uigridlayout(pEx,[2 2]);
    uibutton(gEx, 'Text', 'Passa-Baixas (LPF)', 'ButtonPushedFcn', @(~,~) setExample('lpf'));
    uibutton(gEx, 'Text', 'Passa-Altas (HPF)', 'ButtonPushedFcn', @(~,~) setExample('hpf'));
    uibutton(gEx, 'Text', 'Passa-Banda (BPF)', 'ButtonPushedFcn', @(~,~) setExample('bpf'));
    uibutton(gEx, 'Text', 'Rejeita-Banda (Notch)', 'ButtonPushedFcn', @(~,~) setExample('notch'));

    pOpt = uipanel(left,'BackgroundColor',fig.Color,'BorderType','none');
    optGrid = uigridlayout(pOpt,[1 2]); optGrid.Padding = [0 0 0 0];
    uicheckbox(optGrid, 'Text','Comparar com bandwidth()', 'Value', true, 'FontColor',[1 1 1], 'Tag', 'cbShowBW');
    uicheckbox(optGrid, 'Text','Marcar 0 dB', 'Value', true, 'FontColor',[1 1 1], 'Tag', 'cbMark0dB');

    pRes = uipanel(left,'Title','Resultados da Análise','FontWeight','bold','ForegroundColor',[1 1 1],'BackgroundColor',fig.Color);
    gRes = uigridlayout(pRes,[1 1]);
    outTxt = uitextarea(gRes,'Editable','off','FontName','Consolas','FontSize',11,...
        'BackgroundColor',[0.1 0.1 0.12],'FontColor',[1 1 1]);

    btnGrid = uigridlayout(left,[1 2]); btnGrid.Padding = [0 0 0 0];
    uibutton(btnGrid,'Text','Analisar Sistema','FontWeight','bold', ...
        'ButtonPushedFcn',@(~,~)runAnalysis(), 'BackgroundColor',[0.2 0.4 0.8], 'FontColor',[1 1 1]);
    uibutton(btnGrid,'Text','Limpar Tudo','FontWeight','bold', ...
        'ButtonPushedFcn',@(~,~)limpar(), 'BackgroundColor',[0.4 0.4 0.4], 'FontColor',[1 1 1]);

    %% ---- Lado direito (gráficos)
    right = uigridlayout(gl,[3 1]);
    right.Padding = [8 8 8 8];
    axMag   = uiaxes(right); setDark(axMag); title(axMag,'Diagrama de Bode – Magnitude');
    axPhase = uiaxes(right); setDark(axPhase); title(axPhase,'Diagrama de Bode – Fase');
    axPZ    = uiaxes(right); setDark(axPZ); title(axPZ,'Plano-s (Zeros e Polos)');

    runAnalysis(); % Executa uma análise inicial com o exemplo LPF.

    %% ---- Funções Aninhadas

    function runAnalysis()
        try
            sys = construirTF(eNum.Value, eDen.Value, eZ.Value, eP.Value, eK.Value, eSym.Value);
        catch ME
            uialert(fig,ME.message,'Entrada inválida'); return
        end
        sys = minreal(sys, 1e-9);
        if ~isproper(sys)
            uialert(fig,'Sistema impróprio (grau do numerador > grau do denominador).','Sistema impróprio');
            return
        end
        if any(real(pole(sys)) >= -1e-9)
            uialert(fig,'Atenção: Sistema instável ou marginalmente estável (polos em Re(s)≥0).','Sistema Instável');
        end

        % ===== Análise de Filtro Generalizada =====
        [w, wmin, wmax] = faixaFreqAdaptativa(sys, 10000, 4, 3);
        resultados = analisarFiltro(sys, w);
        % ---- Plotagem: Bode (Magnitude)
        cla(axMag); setDark(axMag); grid(axMag,'on'); hold(axMag,'on');
        plot(axMag, w, 20*log10(resultados.mag), 'LineWidth', 1.8, 'Color', [0.3 0.7 1.0]);
        if findobj(fig, 'Tag', 'cbMark0dB').Value
            yline(axMag, 0, ':', '0 dB', 'LabelHorizontalAlignment','left', 'Color', [0.7 0.7 0.7]);
        end

        % Marcações de -3dB e Pico
        if isfinite(resultados.ganhoPico)
            yline(axMag, 20*log10(resultados.ganhoPico),'-.','Ganho de Pico','Color',[0.9 0.6 0.1], 'LabelVerticalAlignment','top');
        end
        cores_corte = {[0.8 0.8 0.2], [0.2 0.8 0.8]};
        for i=1:numel(resultados.wc)
            label_txt = sprintf('fc%d', i);
            xline(axMag, resultados.wc(i), '-.', label_txt, 'LabelOrientation','horizontal', ...
                'LabelVerticalAlignment','bottom', 'Color', cores_corte{mod(i-1,2)+1}, 'LineWidth',1.1);
        end
        if findobj(fig, 'Tag', 'cbShowBW').Value
            try
                bw_val = bandwidth(sys);
                if isfinite(bw_val), xline(axMag, bw_val, ':', 'bandwidth()', 'Color', [1 0.5 1]); end
            catch, end
        end
        set(axMag,'XScale','log'); xlim(axMag,[wmin wmax]);
        ylabel(axMag,'Magnitude (dB)'); xlabel(axMag,'Frequência (rad/s)');
        title(axMag,'Diagrama de Bode – Magnitude');
        % ---- Plotagem: Bode (Fase)
        cla(axPhase); setDark(axPhase); grid(axPhase,'on'); hold(axPhase,'on');
        plot(axPhase, w, resultados.phase, '--', 'LineWidth', 1.4, 'Color', [1.0 0.7 0.3]);
        set(axPhase,'XScale','log'); xlim(axPhase,[wmin wmax]);
        ylabel(axPhase,'Fase (graus)'); xlabel(axPhase,'Frequência (rad/s)');
        title(axPhase,'Diagrama de Bode – Fase');
        % ---- Plotagem: Plano-s
        cla(axPZ); setDark(axPZ); grid(axPZ,'on'); hold(axPZ,'on'); axis(axPZ, 'equal');
        z = resultados.z; p = resultados.p;
        xline(axPZ,0,':','Color',[0.7 0.7 0.7]); yline(axPZ,0,':','Color',[0.7 0.7 0.7]);
        if ~isempty(z)
            plot(axPZ, real(z), imag(z), 'o', 'DisplayName', 'Zeros', 'MarkerSize', 9, 'LineWidth', 2.2, ...
                    'MarkerEdgeColor', [0 1 1], 'MarkerFaceColor', 'none');
        end
        if ~isempty(p)
            plot(axPZ, real(p), imag(p), 'x', 'DisplayName', 'Polos', 'MarkerSize', 10, 'LineWidth', 2.2, ...
                    'Color', [1 0.3 0.3]);
        end
        xlabel(axPZ,'Eixo Real (σ)'); ylabel(axPZ,'Eixo Imaginário (jω)');
        if ~isempty(z) || ~isempty(p)
            legend(axPZ, 'TextColor',[1 1 1], 'Location','best', 'Color', [0.2 0.2 0.2]);
        end
        fitPlaneLimits(axPZ, z, p);
        title(axPZ,'Plano-s (Zeros e Polos)');
        % ---- Exibição dos Resultados Textuais
        displayResults(resultados);
    end

    function res = analisarFiltro(sys, w)
        % Coleta de dados básicos
        [mag, phase] = bode(sys, w);
        res.mag = squeeze(mag);
        res.phase = squeeze(phase);
        [num, den] = tfdata(sys, 'v');
        res.num = stripLeadingZeros(num);
        res.den = stripLeadingZeros(den);
        res.degNum = max(0, numel(res.num)-1);
        res.degDen = max(0, numel(res.den)-1);
        res.z = zero(sys);
        res.p = pole(sys);
        % Identificação do tipo de filtro
        G0_dB = 20*log10(abs(dcgain(sys)));
        Ginf_dB = 20*log10(abs(freqresp(sys, w(end))));
        [magPico_dB, idx_pico] = max(20*log10(res.mag));

        res.ganhoPico = 10^(magPico_dB/20);
        res.wPico = w(idx_pico);

        dB_threshold = 10; % Limiar para considerar um ganho "baixo"
        if magPico_dB - G0_dB < dB_threshold && Ginf_dB < magPico_dB - dB_threshold
            res.tipo = 'Passa-Baixas (LPF)';
            ganho_ref = abs(dcgain(sys));
        elseif magPico_dB - Ginf_dB < dB_threshold && G0_dB < magPico_dB - dB_threshold
            res.tipo = 'Passa-Altas (HPF)';
            ganho_ref = abs(freqresp(sys, w(end)));
        elseif G0_dB < magPico_dB - dB_threshold && Ginf_dB < magPico_dB - dB_threshold
            res.tipo = 'Passa-Banda (BPF)';
            ganho_ref = res.ganhoPico;
        elseif G0_dB > magPico_dB - dB_threshold && Ginf_dB > magPico_dB - dB_threshold
            res.tipo = 'Rejeita-Banda (BSF)';
            ganho_ref = abs(dcgain(sys));
        else
            res.tipo = 'Tipo Indefinido';
            ganho_ref = res.ganhoPico;
        end
        % Cálculo das frequências de corte
        mag_alvo = ganho_ref / sqrt(2);
        res.wc = findCutoffFrequencies(sys, w, res.mag, mag_alvo);
        res.fc = res.wc / (2*pi);

        % Cálculo de parâmetros adicionais
        res.f0 = NaN; res.w0 = NaN; res.BW_Hz = NaN; res.BW_rad = NaN; res.Q = NaN;
        if numel(res.wc) == 2
            res.w0 = sqrt(res.wc(1) * res.wc(2)); % Freq. central (geométrica)
            res.f0 = res.w0 / (2*pi);
            res.BW_rad = res.wc(2) - res.wc(1);   % Largura de banda
            res.BW_Hz = res.fc(2) - res.fc(1);
            res.Q = res.w0 / res.BW_rad;          % Fator de qualidade
        end
    end

    function displayResults(r)
        Gstr = ['G(s) = (', poly2str(r.num,'s'), ')/(', poly2str(r.den,'s'), ')'];
        zstr = mat2strC(r.z); pstr = mat2strC(r.p);

        out = {Gstr, '', ...
               ['Zeros: ' zstr], ['Polos: ' pstr], '', ...
               sprintf('Grau Numerador = %d', r.degNum), ...
               sprintf('Grau Denominador = %d', r.degDen), ...
               sprintf('Grau Relativo = %d', r.degDen-r.degNum), ...
               '----------------------------------------', ...
               sprintf('Tipo de Filtro: %s', r.tipo),...
               sprintf('Pico de Ganho: %.4g (%.2f dB) @ %.4g rad/s', r.ganhoPico, 20*log10(r.ganhoPico), r.wPico), ...
               ''};
        if ~isempty(r.wc)
            for i=1:numel(r.wc)
                out{end+1} = sprintf('f_c%d (-3dB): %.5g Hz (ω_c%d = %.5g rad/s)', i, r.fc(i), i, r.wc(i));
            end
        else
            out{end+1} = 'Frequência(s) de corte não encontrada(s).';
        end
        if numel(r.wc) == 2
            out{end+1} = '';
            out{end+1} = sprintf('Frequência Central: %.5g Hz (ω₀ = %.5g rad/s)', r.f0, r.w0);
            out{end+1} = sprintf('Largura de Banda:   %.5g Hz (BW = %.5g rad/s)', r.BW_Hz, r.BW_rad);
            out{end+1} = sprintf('Fator de Qualidade (Q): %.4g', r.Q);
        end
        outTxt.Value = out;
    end

    function limpar()
        eNum.Value = ''; eDen.Value = ''; eZ.Value = ''; eP.Value = ''; eK.Value = '1'; eSym.Value = '';
        outTxt.Value = '';
        cla(axMag,'reset'); cla(axPhase,'reset'); cla(axPZ,'reset');
        arrayfun(@(ax) setDark(ax), [axMag, axPhase, axPZ]);
        arrayfun(@(ax) grid(ax, 'on'), [axMag, axPhase, axPZ]);
        title(axMag,'Diagrama de Bode – Magnitude');
        title(axPhase,'Diagrama de Bode – Fase');
        title(axPZ,'Plano-s (Zeros e Polos)');
    end

    function setExample(type)
        limpar();
        switch lower(type)
            case 'lpf' % Butterworth 2ª ordem, fc=1kHz
                eNum.Value = '[1]';
                eDen.Value = '[1/(2*pi*1000)^2 sqrt(2)/(2*pi*1000) 1]';
            case 'hpf' % Butterworth 2ª ordem, fc=500Hz
                w_c = 2*pi*500;
                eSym.Value = sprintf('s^2 / (s^2 + %f*s + %f)', sqrt(2)*w_c, w_c^2);
            case 'bpf' % fc=2kHz, Q=5
                w0 = 2*pi*2000; Q = 5; BW = w0/Q;
                eSym.Value = sprintf('(%f*s) / (s^2 + %f*s + %f)', BW, BW, w0^2);
            case 'notch' % Notch em 60Hz, Q=30
                w0 = 2*pi*60; Q = 30; BW = w0/Q;
                eSym.Value = sprintf('(s^2 + %f) / (s^2 + %f*s + %f)', w0^2, BW, w0^2);
        end
        runAnalysis();
    end

    function sys = construirTF(strNum,strDen,strZ,strP,strK,strSym)
        if ~isempty(strtrim(strSym))
            if isempty(regexp(strSym, '^[\s0-9\.\+\-\*\/\^\(\)spi]+$', 'once'))
                error('Expressão inválida. Use apenas s, números, pi e operadores + - * / ^ ( ).');
            end
            s = tf('s');
            try
                sys = eval(strSym);
            catch ME
                error('Não foi possível avaliar a expressão: %s', ME.message);
            end
            if ~isa(sys,'tf'), error('A expressão não resultou em uma função de transferência.'); end
            return
        end
        if ~isempty(strtrim(strZ)) || ~isempty(strtrim(strP))
            z = parseVetor(strZ,'zeros');
            p = parseVetor(strP,'polos');
            k = str2double(strK);
            if isempty(p), error('Informe ao menos um polo para construir por Z/P/K.'); end
            if isnan(k), k=1; warning('Ganho k inválido, usando k=1.'); end
            sys = zpk(z,p,k);
            return
        end
        if ~isempty(strtrim(strNum)) && ~isempty(strtrim(strDen))
            num = parseVetor(strNum,'numerador');
            den = parseVetor(strDen,'denominador');
            if isempty(den) || all(abs(den)<eps), error('Denominador inválido.'); end
            sys = tf(num,den);
            return
        end
        error('Preencha uma das três seções de entrada para continuar.');
    end

    function v = parseVetor(txt,rot)
        if isempty(strtrim(txt)), v = []; return, end
        v = str2num(txt);
        if ~isnumeric(v) || ~isvector(v)
            error('Entrada inválida em %s. Use formato MATLAB, ex.: [1 2 3].',rot);
        end
        v = double(v(:)).';
    end

    function setDark(ax)
        ax.Color = [0.12 0.12 0.15];
        ax.XColor = [0.9 0.9 0.9];
        ax.YColor = [0.9 0.9 0.9];
        ax.GridColor = [0.35 0.35 0.35];
        ax.MinorGridColor = [0.25 0.25 0.25];
        ax.Title.Color = [1 1 1];
        ax.XLabel.Color = [0.9 0.9 0.9];
        ax.YLabel.Color = [0.9 0.9 0.9];
        ax.Box = 'on';
        ax.FontName = 'Arial';
    end

    function s = mat2strC(v)
        if isempty(v), s = '[]'; return, end
        s = '[';
        for k=1:numel(v)
            if imag(v(k)) == 0
                s = [s, sprintf('%g', real(v(k)))];
            elseif real(v(k)) == 0
                s = [s, sprintf('%gj', imag(v(k)))];
            else
                s = [s, sprintf('%g%+gj', real(v(k)), imag(v(k)))];
            end
            if k<numel(v), s = [s, ', ']; end
        end
        s = [s, ']'];
    end

    function v = stripLeadingZeros(v)
        i = find(abs(v)>eps,1,'first');
        if isempty(i), v = 0; else, v = v(i:end); end
    end

    function w_cortes = findCutoffFrequencies(sys, w, mag, target_mag)
        w_cortes = [];
        crossings = find(diff(sign(mag - target_mag)) ~= 0);
        if isempty(crossings), return; end

        f_mag = @(ww) abs(squeeze(freqresp(sys, ww))) - target_mag;

        for i = 1:numel(crossings)
            idx = crossings(i);
            w_interval = [w(idx), w(idx+1)];
            try
                wc = fzero(f_mag, w_interval);
                if isreal(wc) && isfinite(wc) && wc > 0
                    w_cortes(end+1) = wc;
                end
            catch
                % fzero pode falhar se os sinais nos extremos do intervalo
                % não forem opostos. Isso pode acontecer perto de picos.
                % Ignorar falha e continuar para o próximo cruzamento.
            end
        end
        w_cortes = sort(unique(w_cortes));
    end

    function [w, wmin, wmax] = faixaFreqAdaptativa(sys, npts, decFolgaHi, decFolgaLo)
        if nargin < 2 || isempty(npts),      npts = 8000; end
        if nargin < 3 || isempty(decFolgaHi), decFolgaHi = 4; end
        if nargin < 4 || isempty(decFolgaLo), decFolgaLo = 3; end

        zp = [zero(sys); pole(sys)];
        w_zp = abs(zp(isfinite(zp) & zp~=0));

        if isempty(w_zp)
            wmin = 1e-3; wmax = 1e7;
        else
            wmin0 = min(w_zp);
            wmax0 = max(w_zp);
            wmin = 10^(floor(log10(wmin0)) - decFolgaLo);
            wmax = 10^(ceil(log10(wmax0)) + decFolgaHi);
            wmin = max(wmin, 1e-9);
            if wmax <= wmin*100, wmax = wmin*100; end
        end
        w = logspace(log10(wmin), log10(wmax), npts);
    end

    function fitPlaneLimits(ax, z, p)
        pts = [z(:); p(:)];
        if isempty(pts)
            xlim(ax,[-1 1]); ylim(ax,[-1 1]); return
        end

        real_pts = real(pts(isfinite(pts)));
        imag_pts = imag(pts(isfinite(pts)));

        % Incluir a origem para garantir que o plano-s esteja centrado
        all_x = [0; real_pts];
        all_y = [0; imag_pts];

        xr = [min(all_x), max(all_x)];
        yi = [min(all_y), max(all_y)];

        % Calcula o maior range (horizontal ou vertical)
        range_x = diff(xr);
        range_y = diff(yi);
        max_range = max(range_x, range_y);

        % Aplica uma margem de 15% ao maior range
        margin = max_range * 0.15;

        % Centraliza os limites no maior range
        center_x = mean(xr);
        center_y = mean(yi);

        xlim(ax, [center_x - (max_range/2 + margin), center_x + (max_range/2 + margin)]);
        ylim(ax, [center_y - (max_range/2 + margin), center_y + (max_range/2 + margin)]);
    end
end
